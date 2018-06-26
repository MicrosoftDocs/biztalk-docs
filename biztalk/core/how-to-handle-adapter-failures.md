---
title: "How to Handle Adapter Failures | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bdceb364-38d6-4aab-a176-bf751da1be25
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Handle Adapter Failures
In general, adapters should suspend messages that they cannot process. For example, a receive adapter that experiences a submit failure should typically suspend the messages, although this decision depends upon the purpose of the adapter. There are also security considerations around handling failures. For example, if an adapter automatically suspends all failed messages, the adapter might be open to a denial-of-service attack that causes the BizTalk Server Suspended queue to fill up.  Some adapters, such as HTTP, can return a failure code to the client indicating that the request has been rejected. For these types of adapters it often makes sense to return a failure code rather than suspend the message. Typically send adapters only suspend messages after all of the retries have been exhausted for both primary and secondary transports.  
  
## Associate Error Processing with an Individual Operation and Not with the Batch That Contains the Operation  
 The batching of messages within an adapter should be invisible to the user of the adapter. This means that the failure of one operation in a batch should not affect any other operation in any way. However, batches are atomic, so the failure of one message results in an error for the batch, and no operations are processed.  
  
 You write the code that is responsible for handling the error, resubmitting the successful messages, and suspending the unsuccessful ones. Fortunately, BizTalk Server provides a detailed error structure that enables your adapter to determine the specific operation that failed. It permits construction of further batches in which the successful operations are resubmitted and the unsuccessful ones suspended.  
  
 The final state of the operation should not be affected by the batching within the adapter.  
  
## Use SetErrorInfo to Report Failure to BizTalk Server  
 If you are suspending a message, you must provide failure information to BizTalk Server from the previous message context. BizTalk Server provides error reporting capabilities using the **SetErrorInfo** method on both the **IBaseMessage** and **ITransportProxy** interfaces. You can report errors as follows:  
  
- When a failure occurs while processing a message, set the exception using **SetErrorInfo(Exception e)** on the message (**IBaseMessage**) to be suspended. This allows the engine to preserve the error with the message for later diagnosis and logs it to the event log to alert the administrator.  
  
- If you encounter an error during initialization or internal bookkeeping (not during message processing) you should call **SetErrorInfo(Exception e)** on the **ITransportProxy** pointer that was passed to you during initialization. If your adapter is based on the BaseAdapter implementation, you should always have access to this pointer. Otherwise, you should be certain that you cache it.  
  
  Reporting an error with either of these methods results in the error message being written to the event log. It is important that you associate the error with the related message if you are able to do so.  
  
## Handle a Database-Offline Condition  
 If one of the BizTalk Server databases goes offline, the BizTalk service recycles itself. The Messaging Engine makes a best effort to shut down all of the receive locations before recycling the service. If this takes longer than 60 seconds, the service terminates. Because the engine is transacted, this does not cause data loss.  
  
 This time-out can be tuned in the registry by using the key:  
  
```  
DWORD   
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\BTSSvc{Host Guid}\MessagingDBFailoverShutdownTimeLimit  
```  
  
 For isolated adapters, because BizTalk Server does not own the process, the receive locations are disabled when one of the BizTalk Server databases goes offline. After the database comes back online those receive locations are re-enabled.  
  
## Write to the Event Log  
 The adapter can write event log entries by using the **IBTTransportProxy** interface passing in an exception. Adapters developed in native code need to pass in an **IErrorInfo** interface, **IBTTransportProxy.SetErrorInfo( Exception** `e` **)**.  
  
 The Messaging Engine writes to the event log on behalf of the adapter for events such as when an adapter retries a message after transmission failure, moves a message to its backup transport, or suspends a message. For operations such as these the adapter only needs to set the exception on the message before calling the API. The following code fragment demonstrates this:  
  
```  
IBaseMessage msg;  
...  
// Set exception on msg to indicate why transmission failed...  
msg.SetErrorInfo(  
 new ApplicationException(  
 "The TCP connection was closed by the destination"));  
```  
  
## Handle Receive-Specific Batch Errors  
  
### Handle Receive Failures  
 When an adapter submits an operation (or batch of operations) to BizTalk Server there can be various reasons for failure. The two most significant are:  
  
- The receive pipeline failed.  
  
- A routing failure occurred while publishing a message.  
  
  The Messaging Engine automatically tries to suspend the message when it gets a receive pipeline failure. The suspend operation may not always be successful. For example, if the Messaging Engine hits a routing failure while publishing a message, then the engine does not even try to suspend the message.  
  
  It is always possible that a message will fail. In such a situation, the adapter should explicitly call the **MoveToSuspendQ** API and should try to suspend the message. When an adapter tries to suspend a message, one of the following should be true:  
  
- The same message object that the adapter submitted (recommended) should be suspended.  
  
- If the adapter has to create a new message, then it should set the message context of the new message with the pointer to the message context of the message that was originally submitted. This is because the message context of a message has a lot of valuable information about the message and the failure. This information is required to debug the failed message.  
  
> [!NOTE]
>  If the adapter creates a new message object and suspends it, the adapter should copy the error information from the old message object to the new message object.  
  
 Some adapters, such as the HTTP adapter provided with BizTalk Server, do not require that the message be suspended. These adapters can return an error back to their client.  
  
#### Causes of failure  
 Simple causes of failure are the errors that can occur as the batch is constructed or when **IBTTransportBatch::Done** is called.  
  
-   **Submit failure.** The **Submit** call can fail for a limited number of reasons, and all of them are fatal. These reasons include:  
  
-   Out-of-memory errors occurring in the BizTalk Server process space.  
  
-   The schema assembly has been dropped from the deployment. In this case, the **Submit** fails with a cryptic error. In the MQSeries adapter, the generic failure exception from BizTalk Server is caught, and an extended error message is written in the system event log. This message suggests that one of the possible causes of the error is that the schema assembly has somehow been dropped from the deployment.  
  
     In general, if **Submit** fails you should try to suspend the message using the same transaction.  
  
-   **IBTTransportBatch::Done failure.** The **IBTTransportBatch::Done** call can fail for one of several reasons. In general, you should always attempt one suspend operation and end the transaction only if that fails. One of the error codes you might receive from the failure of **IBTTransportBatch::Done** is that BizTalk Server is trying to shut down. In this case, you should just end the transaction and leave it because the **Terminate** call is probably happening concurrently. Other scenarios occur when you have successfully constructed the batch and successfully executed **IBTTransportBatch::Done**. In these cases, the errors are returned in **BatchComplete** and the adapter must determine what to do with them. The rest of this section deals with this case.  
  
#### Processing BatchComplete errors  
 **BatchComplete** is a callback provided by the adapter that is invoked by BizTalk Server to indicate the completion status of a batch operation.  
  
 The most important parameter passed to **BatchComplete** is the batch status `hResult`. This indicates success or failure for the batch. If the batch failed, it means that none of the operations in the batch succeeded. The adapter goes through the batch status structure and determines which messages failed (this is known as *filtering the batch*).  
  
#### Nontransactional BatchComplete errors  
 For nontransactional adapters, you must choose your response if a failure occurs for a **SubmitMessage**/**SubmitRequestMessage** or **SubmitResponseMessage** operation. Typically adapters suspend the message by calling **MoveToSuspendQ**.  
  
 The following operations are always expected to pass: **DeleteMessage**, **MoveToSuspendQ**, **ResubmitMessage**. If these operations fail, it typically means that there is a bug in the adapter. You do not have to write code to handle a failure in these cases. However if the batch failed because another operation failed, then these operations must be re-executed in a fresh batch.  
  
 If the adapter calls **MovetoBackupTransport** and that fails (because there was no backup transport), then the adapter should call **MoveToSuspendQ** to suspend the message.  
  
#### Transactional BatchComplete errors  
 When you submit batches to BizTalk Server using a transaction created by the adapter, you should follow one of these two scenarios:  
  
-   **Use single-message batches.** Send a single-message batch to BizTalk Server. If that single message fails, then you can legally send BizTalk Server a second batch under the same transaction, but you must move the offending message to the Suspended queue rather than resubmitting it. After the failed message is removed, the submission of the second batch should succeed. After that occurs you can commit the transaction when BizTalk Server confirms that the second batch was successful. If the second batch fails, the adapter must abort the transaction, or find somewhere else to place that message. In this scenario, you immediately take a significant performance hit due to transaction rollback processing.  
  
     There are some techniques that you can use to improve the performance of the adapter. For example, the MQSeries adapter adjusts its approach dynamically at run time. It runs with 100-message batches. If it hits an error, it must end the batch, but it switches to single-message batches for a short time as it gets past the bad message. It then reverts to 100-message batches. If it hits the error again, it slows down again.  
  
-   **Use preemptive suspension.** Construct a multi-message batch in which the erroneous messages are preemptively suspended. The batch contains a mix of **Submit** and **MoveToSuspendQ** operations, and is the first and only batch under the transaction. It should succeed because the bad data was preemptively suspended, and the transaction can be committed (after waiting to receive the confirmation from BizTalk Server).  
  
     This might seem to require looking into the future, but this technique has been used in the MSMQ adapter. It depends on having reliably unique message IDs. This adapter constructs a batch of messages. If anything fails it rolls back the transaction (and therefore the batch), but remembers the message ID in a temporary data structure. (To prevent this structure from growing indefinitely, items in it are removed after some fixed time delay.) Before each batch is submitted, the adapter checks the list of bad message IDs. If it sees one, it knows that message will fail (because it failed once in the past), and preemptively suspends it rather than trying to submit it.  
  
     Not every adapter has a reliably unique message ID, and a transactional store is less likely to have one. Because of this, many transactional adapters are restricted to sending single-message batches.  
  
#### Processing other errors  
 In all other cases (such as failures in suspending messages), the adapter must end the transaction. Any other outcome results in either duplicate or dropped messages.  
  
 Whenever the adapter can, it should abort the transaction if a batch fails. However there are scenarios where the adapter cannot abort the transaction. In such a scenario it should suspend the message using the same transaction.  
  
#### Processing errors on transactional receive  
 A common transactional processing pattern is to end a transaction when an error occurs. In this case everything returns to its previous state and no data is lost. However, if you are consuming data from a transactional feed (for example, pulling a row at a time from a staging table in a database, or pulling one message at a time from a queuing product like MQSeries or MSMQ), then this might not be enough. If you simply end the transaction and go back and pick up the same data again, the same error is likely to occur and the system becomes stuck in a repeated loop.  
  
 The SQL adapter in an earlier version of BizTalk Server shipped with this behavior. However, soon after release the adapter behavior was changed to attempt to suspend a failed message and commit the transaction. Moving a message to the Suspended queue under the same transaction and then committing the transaction saves the data from being lost and also allows the adapter to get past bad data.  
  
 When the receive portion of an adapter is passed an error message in response to a **Submit** message operation, the adapter should process that error and move the message to the Suspended queue.  
  
 In the case of transactional batches in which the adapter has created the transaction object and submits messages under the transaction, the adapter should logically move the message to the Suspended queue under the same transaction when failures occur. The transaction ensures that data is not dropped, and even data that is causing an error should never be dropped.  
  
### Handle Messages without Subscriptions  
 BizTalk Server does not accept a message to be published in its MessageBox database if there are no subscriptions defined to accept it. Subscriptions are registered by either orchestrations or send ports. Multiple subscriptions can be defined, in which case the message is sent to multiple destinations. If there are no subscriptions, BizTalk Server rejects the message and does not attempt to suspend it. If the adapter does not handle this error and explicitly suspend the message, then the message is dropped and its data is potentially lost. Of course a transactional adapter may end the transaction and return the message to its destination.  
  
### Support Seek with Your Receive Stream  
 The receive-side stream must support the **Seek** method for BizTalk Server to be able to suspend the message on a pipeline failure. If the message stream is not seekable, then BizTalk Server generates an error when it tries to run **Seek**.  
  
 In many cases supporting **Seek** is not easy. When streaming data from a network, for example, it may be difficult to go back to the network resource and request the data again.  
  
 Several adapters that ship with BizTalk Server spool the message data onto a file on disk at the same time as BizTalk Server reads the data. This allows the adapter to use **Seek** on that file if it encounters an error (in the pipeline processing of the message data, for example). Internally the adapter uses the **ReadOnlySeekableStream** class that wraps an incoming non-seekable stream and overflows to disk when a configurable size threshold is reached. For messages smaller than the threshold size, the disk is never hit.  
  
### Consider User-Configurable Error-Handling Options  
 Sometimes there is no one correct response to an error. In this case, you should consider a user-configurable option to choose between behaviors. The MQSeries adapter does this.  
  
 The problem with having the adapter suspend messages when it sees an error is that the Suspended queue in BizTalk Server is something of a "black hole." It is relatively easy to get messages into the queue, but harder to get them out again.  
  
 Some users of the adapter might not want anything in the Suspended queue. For example, in the case of the MQSeries adapter, the user is offered a configuration option to do one of the following:  
  
-   Set the adapter to end the current transaction and disable itself when it sees an error.  
  
-   Suspend the failed message and commit the transaction. The adapter does this even when BizTalk Server has successfully suspended the message. This action meets the requirements of the customer even if it causes the event log to not be strictly correct.  
  
### Implement Receive Ordering by Using a Single Thread and Waiting on BatchComplete  
 The interface to BizTalk Server is designed for performance and the ability to scale out by supporting concurrency. However, if you want a strictly ordered receive of messages (as is sometimes required when receiving messages from a message queue product like MQSeries or MSMQ), then you must do some additional work in the adapter to disable some of that concurrency. This can be done in two steps:  
  
1. You must use a single thread for all the data processing in the adapter.  
  
2. You must wait for BizTalk Server to completely process each batch. This requirement is important and can be accomplished by using .NET thread synchronization primitives. For example, using an **AutoResetEvent**, you would:  
  
   -   Declare the event object where it can be accessed by both the main worker thread and the **BatchComplete** callback object.  
  
   -   On the main worker thread, submit the messages to the batch as usual but then call **AutoResetEvent.Reset** on the event object just before the call to the batch **IBTTransportBatch::Done**.  
  
   -   Call **AutoResetEvent.WaitOne** on the event object from this same thread. This causees the main worker thread to block. In the **BatchComplete** callback from BizTalk Server you then call **AutoResetEvent.Set** on the same event object to unblock the worker thread so it is ready to process another message.  
  
   It is strongly suggested that *receive ordering* like this be made configurable because it causes significant performance degradation. Many, if not most, user scenarios do not require ordering of messages. Suspending messages can also break ordering. Exactly what to do in this case is application-dependent, so the best thing for your adapter to do is to offer the user a configuration point.  
  
   In ordered scenarios, some customers have stated that they would prefer to stop the processing, that is, disable the adapter, rather than break ordering. The MQSeries adapter, which supports ordered receive, provides this option to the user.  
  
## Handle Send-Specific Batch Errors  
  
### Handle Send Retry and Batching  
 Here is a typical example of send-side batching:  
  
- BizTalk Server gives a batch of messages to the adapter.  
  
- When the adapter determines that it has given the message to its destination correctly, it executes delete back on BizTalk Server indicating that it is done. (As usual, several delete messages can be arbitrarily batched up to improve performance.)  
  
  If the send-side adapter fails to process a message, then it may do one of several things with that message:  
  
- The adapter should tell BizTalk Server that it wants a message retried. BizTalk Server does not automatically retry a message. BizTalk Server keeps a count of the retries, and this count can be seen in the message context.  
  
- The adapter may determine that it cannot process a message. In this case, the adapter might move the message to the next transport. The adapter does this with the **MoveToNextTransport** call on the **Batch** object.  
  
- The adapter may move the message to the Suspended queue.  
  
  The adapter determines what happens to the message. However, it is recommended that you have adapters behave in a consistent manner because this makes a BizTalk Server installation easier to support.  
  
  It is highly recommended that adapters behave as described below. The adapters shipped with BizTalk Server behave like this.  
  
### Recommended Behavior for Handling Send Errors in a Batch  
 The send adapter receives some messages and submits them to BizTalk Server.  
  
 For each successful message the adapter should delete that message on BizTalk Server. All communication back to BizTalk Server is done through batches, and the deletes can be batched up. They do not have to be the same batch that BizTalk Server created on the adapter. If there are any response messages (as in a SolicitResponse scenario), then they should be submitted back to BizTalk Server (with SubmitResponse) along with the associated delete.  
  
- If the message processing in the adapter was unsuccessful, check the retry count.  
  
  -   If the retry count was not exceeded, resubmit the message to BizTalk Server, remembering to set the retry time on the message. The message context provides the retry count and the retry interval the adapter should use.  
  
  -   If the retry count was exceeded, then the adapter should attempt to move the message by using **MoveToNextTransport**. The resubmit and **MoveToNextTransport** messages can be mixed with the deletes in the same batch back to BizTalk Server. This is not required, but can be a useful step.  
  
- The resubmit and the **MoveToNextTransport** are ways for the adapter to deal with failures. But there can be a failure within the processing of the failure. In this case, in processing the response from BizTalk Server (in the **BatchComplete** method) the adapter must create another batch against BizTalk Server to indicate what to do with that failure.  
  
   Follow these steps when processing a failure that occurs within the processing of another failure:  
  
  -   If the resubmit fails, use **MoveToNextTransport**.  
  
  -   If the **MoveToNextTransport** fails, use **MoveToSuspendQ**.  
  
  You must keep creating batches on BizTalk Server until you receive a successful action back on BizTalk Server.  
  
### Serialization of Message Context Property  
 All objects assigned to a message context property must be serializable. Otherwise the Messaging Engine will throw an exception of type **E_NOINTERFACE**. This return value ambiguously represents a non-serializable object attempting to be assigned the message context.