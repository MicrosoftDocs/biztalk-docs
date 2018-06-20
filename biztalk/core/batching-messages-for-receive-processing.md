---
title: "Batching Messages for Receive Processing | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 32bf0b70-e9d1-4fab-9c74-160e51390700
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Batching Messages for Receive Processing
## Batch Callbacks  
 Batches submitted by receive adapters to the Messaging Engine are processed asynchronously. Therefore the adapter needs a mechanism to tie a callback to some state in the adapter so it can be notified of success or failure and perform any necessary cleanup actions. The callback semantics are flexible such that adapters can use one or a combination of three approaches. These are:  
  
- All callbacks are made on the same object instance that implements **IBTBatchCallBack**.  
  
- The cookie passed into the engine when requesting a new batch is used to correlate the callback to the state in the adapters.  
  
- There is a different callback object for each batch that implements **IBTBatchCallBack**. Here each object holds its own private state.  
  
  When the batch has been processed, the adapter is called back on its implementation of **IBTBatchCallBack.BatchComplete**. The overall status of the batch is indicated by the first parameter, the HRESULT status. If this value is greater than or equal to zero, then the batch was successful in the sense that the engine has ownership of the data and the adapter is free to delete that data from the wire. A negative status indicates that the batch failed: None of the operations in the batch were successful and the adapter is responsible for handling the failure.  
  
  If the batch failed, then the adapter needs to know which item in which operation failed. For example, suppose that the adapter was reading 20 files from disk and submitting them into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] using a single batch. If the tenth file was corrupted, the adapter would need to suspend that one file and resubmit the remaining 19. This information is available to the adapter in the second and third parameters—`opCount` (operation count) of type short and `operationStatus`, which is of type BTBatchOperationStatus[].  
  
> [!NOTE]
>  On a single batch object you should never submit a message more than once. Submitting the same message object more than once on the same batch will result in engine errors.  
  
 The operation count indicates how many types of operations were in the batch (the size of the **BTBatchOperationStatus** array). Each element in the operation status array corresponds to a given operation type. By using the **BTBatchOperationStatus** array, the adapter can determine which item in a given operation failed by looking at the **BTBatchOperationStatus.MessageStatus** array for negative HRESULT values signifying failure. In the scenario above, the adapter creates a new batch containing 19 message submits and one message suspend.  
  
 The following code fragment shows how an adapter requests a new batch from the engine through its transport proxy and submits a single message into the engine using the cookie approach. The Messaging Engine calls the **BatchComplete** method as the batch callback when it has completed processing the entire batch of submitted messages.  
  
```  
using Microsoft.BizTalk.TransportProxy.Interop;  
using Microsoft.BizTalk.Message.Interop;  
  
public class MyAdapter :   
                  IBTTransport,   
                  IBTTransportConfig,   
                  IBTTransportControl,  
                  IPersistPropertyBag,   
                  IBaseComponent,  
                  IBTBatchCallBack  
{  
      private IBTTransportProxy _tp;  
  
      public void BatchComplete(      
            Int32                         status,   
            Int16                         opCount,   
            BTBatchOperationStatus[]      operationStatus,   
            System.Object                 callbackCookie)  
      {  
            // Use cookie to correlate callback with work done,  
            // in this example the batch is to submit a single  
            // file the name of which will be in the  
            // callbackCookie  
            string fileName = (string)callbackCookie;  
            if ( status >= 0 )  
                  // DeleteFile from disc  
                  File.Delete(fileName);          
            else  
                  // Rename file to fileName.bad  
                  File.Move(fileName, fileName + ".bad");  
      }  
  
      private void SubmitMessage(  
            IBaseMessage                  msg,   
            string                        fileName)  
      {  
            // Note: Pass in the filename as the cookie  
            IBTTransportBatch batch =   
                  _tp.GetBatch(this, (object)fileName);  
  
            // Add msg to batch for submitting   
            batch.SubmitMessage(msg);   
  
            // Process this batch  
            batch.Done(null);  
      }  
}  
```  
  
 The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] SDK includes samples for the following adapters: File, HTTP, MSMQ, and the Transactional Adapter. All of these adapters are built on top of a common building block called the BaseAdapter. Version 1.0.1 of the BaseAdapter includes all of the relevant code to parse the operation status and rebuild a new batch to submit.  
  
## Race Condition  
 The two tasks of resolving errors and deciding the final outcome of a submitted batch seem simple enough, but in fact they rely on information from different threads:  
  
- The adapter processes errors based on information passed by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to the adapter's **BatchComplete** callback method. This callback executes on the adapter's thread.  
  
- **DTCCommitConfirm** is a method on the **IBTDTCCommitConfirm** object. An instance of the **IBTDTCCommitConfirm** object is returned by the batch **IBTTransportBatch::Done** call. This instance is on the same thread as the **IBTTransportBatch::Done** call, which is different from the adapter's callback thread.  
  
  For every call that the adapter makes to **IBTTransportBatch::Done** the Messaging Engine makes a corresponding call to the callback method **BatchComplete** in a separate thread to report the result of the batch submission. In **BatchComplete** the adapter needs to commit or roll back the transaction based on whether the batch passed or failed. In either case, the adapter should then call **DTCCommitConfirm** to report the status of the transaction.  
  
  A possible race condition exists because the adapter’s implementation of **BatchComplete** can assume that the **IBTDTCCommitConfirm** object returned by **IBTTransportBatch::Done** is always available when **BatchComplete** executes. However, **BatchComplete** can be called in a separate Messaging Engine thread, even before **IBTTransportBatch::Done** returns. It is possible that when the adapter tries to access the **IBTDTCCommitConfirm** object as a part of the **BatchComplete** implementation, there is an access violation because that calling thread no longer exists. Use the following solution to avoid this condition.  
  
  In the following example, the problem is solved by using an event. Here the interface pointer is accessed through a property that uses the event. The get always waits for the set to complete before proceeding.  
  
```  
protected IBTDTCCommitConfirm CommitConfirm  
{  
      set  
      {  
            this.commitConfirm = value;  
            this.commitConfirmEvent.Set();  
      }  
      get  
      {  
            this.commitConfirmEvent.WaitOne();  
            return this.commitConfirm;  
      }  
}  
protected IBTDTCCommitConfirm commitConfirm = null;  
private ManualResetEvent commitConfirmEvent = new ManualResetEvent(false);  
```  
  
## Batch Status Codes  
 The overall batch status code indicates the outcome of the batch. The operation status gives the submission status code for individual message items. Batches can fail for various reasons. There might be a security-related failure, or the message might have been submitted when the engine was shutting down. (Typically when the engine shuts down it does not accept any new work but does allow in-process work to be completed.) The following table indicates some common HRESULT values that are returned either in the batch status or the operation status. It also indicates whether these are success or failure codes. The proper handling of these codes is described more fully in [How to Handle Adapter Failures](../core/how-to-handle-adapter-failures.md).  
  
|Code (defined in the class BTTransportProxy)|Success/failure code|Description|  
|----------------------------------------------------|---------------------------|-----------------|  
|BTS_S_EPM_SECURITY_CHECK_FAILED|Success|The port was configured to perform a security check and drop messages that failed authentication. Adapters should not suspend batches that return this status code.|  
|BTS_S_EPM_MESSAGE_SUSPENDED|Success|Indicates that one or more messages were suspended, and the engine has ownership of the data. It is a success code in that the Messaging Engine has accepted the message submission.|  
|E_BTS_URL_DISALLOWED|Failure|A message was submitted with an invalid **InboundTransportLocation**.|  
  
## Batch Operations  
 The following table details the member methods and operations of the **IBTTransportBatch** object that the adapter uses to add work to a given batch.  
  
|Method name|Operation type|Description|  
|-----------------|--------------------|-----------------|  
|**SubmitMessage**|Submit|Submits a message into the engine.|  
|**SubmitResponseMessage**|Submit|Submits a response message into the engine. This is the response message in a solicit-response pair.|  
|**DeleteMessage**|Delete|Deletes a message that an adapter has successfully transmitted over the wire using a non-blocking send. Adapters that use blocking sends do not need to call this method because the Messaging Engine will delete it on the adapter's behalf if the adapter returns `true` from **TransmitMesssage**.|  
|**MoveToSuspendQ**|MoveToSuspendQ|Moves a message into the Suspended queue.|  
|**Resubmit**|Resubmit|Requests that a message should be retried for transmission at a later time. This is typically called after a transmission attempt has failed.|  
|**MoveToNextTransport**|MoveToNextTransport|Requests that a message be transmitted using its backup transport. Typically called after all retries have been exhausted. If no backup transport is present this method will fail|  
|**SubmitRequestMessage**|SubmitRequest|Submits a request message. This is a request message in a request-response pair.|  
|**CancelRequestForResponse**|CancelRequestForResponse|Notifies the engine that the adapter no longer wishes to wait for the response message in a request-response pair.|  
|**Clear**|NA|Clears all work from the batch.|  
|**Done**|NA|Submits a batch of messages to the engine for processing.|  
  
## Batch Management  
 Batches are implemented in native code in the Messaging Engine. For this reason an adapter written in managed code should release the runtime callable wrapper (RCW) for the batch after it has finished with the batch. This is done in managed code by using the **Marshal.ReleaseComObject** API. It is important to remember that this API should be called in a while loop until the returned reference count reaches zero.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processes messages synchronously within a batch. Many batches may be processed concurrently, which may provide an opportunity for some optimization in the adapter by adjusting the batch size in the application domain. For example, you might process all the files on an FTP site (until some limit is hit). In the case of SAP you might process a single stream into a number of messages that are then submitted as a batch.  
  
 The batch used by an adapter to pass operations back to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] does not need to exactly correspond to the list of messages that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] gives to the adapter. In other words, when doing transactional sends you must split the resubmit operations **MoveToNextTransport** and **MoveToSuspendQ** into separate batches. Many adapters sort a batch of messages that have been submitted for multiple endpoints into separate lists of messages for further processing.  
  
 The point is that there are no rules (besides those associated with the transaction) associated with message batching in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Batching is simply an implementation-specific way for the adapter to chunk messages into and out of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 An adapter can batch messages from multiple smaller batches that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] has given it into a larger batch for the response to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. This might be a significant optimization in transactional adapters that are dealing with large numbers of very small messages. It minimizes the "total number of transactions per message" ratio.  
  
 Typically [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] produces send-side batches of between 5 and 10 messages. If these are very small messages, an adapter might batch up to 100 messages or more before it submits a transactional batch of deletes back to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. An optimization like this is not easy to implement; you must make sure that messages never get stuck in the adapter memory, waiting endlessly for some threshold to be met.  
  
 The significance of batching can be seen in the performance numbers for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] for the high-throughput adapters like MQSeries. In these adapters, messages are received at least twice as often as they are sent. By default the receive adapter uses batches of 100 messages and the send adapter uses the default [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] batch it is given.  
  
## Transactional Batches  
 When you write an adapter that creates a transaction object and hands it to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you are accepting responsibility for writing code that does the following:  
  
- Decides the final outcome of the batch operation: to either commit or end the transaction. This may depend upon other transactional branches within the scope of this one transaction that are not [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dependent, such as writing to an Message Queuing (MSMQ) queue or a transactional database operation.  
  
- Informs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] of the final outcome by calling the **IBTDTCCommitConfirm.DTCCommitConfirm** method. Returning `true` indicates a successful commit of the transaction; returning `false` signifies failure and rollback of the transaction.  
  
  The adapter must inform [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] about the final outcome of the transaction to maintain its internal tracking data. The adapter informs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] of the outcome by calling **DTCCommitConfirm**. If the adapter does not do this, a significant memory leak occurs and the MSDTC transaction could time out and fail despite its operations completing successfully.