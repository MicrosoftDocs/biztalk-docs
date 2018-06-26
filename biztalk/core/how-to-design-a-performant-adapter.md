---
title: "How to Design a Performant Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b5a1f338-fd7c-41c8-a181-8da8b293c4cc
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Design a Performant Adapter
For performance purposes all adapters should be batch-aware with regard to submitting batches of messages, transmitting batches, and generally performing operations on messages in batches. Adapters should try to expose configurable performance-related attributes, such as the size of batches or the number of bytes in a batch, that are configurable from the adapter's design-time user interface.  
  
 As mentioned earlier, send adapters should always perform non-blocking sends to avoid degrading the performance of the send host. Further blocking of Messaging Engine APIs is not recommended.  
  
 Writing to and reading from the message context affects run-time performance. In general, adapters should avoid reading, writing, and promoting excessive numbers of message-context properties. Promoting properties creates an additional performance drain because of the subscription evaluation that occurs on each promoted property at run time. However, an adapter would need to promote a huge number of properties to noticeably impact performance. Still it is a good practice to promote only those properties that are required to be promoted.  
  
## Throttle Send and Receive  
 When the load on the BizTalk engine exceeds the configured threshold, the engine throttles adapters and orchestrations to ensure optimum performance. On the receive side, when the workload on the engine exceeds a given threshold, the adapter's call to **IBTTransportBatch.Done** is blocked until the load has decreased sufficiently. This forces the adapter to submit new work into the engine only when the engine is available. On the send side, when the engine is throttling adapters sending outbound messages, the engine does not deliver new messages to be transmitted until its load is reduced.  
  
 For these reasons, the adapter does not need to be concerned with throttling unless it is required, for example, to limit the number of connections to a back-end system. For these types of scenarios, neither the engine nor the Adapter Framework provides any support.  
  
 You can handle throttling the number of messages sent from a custom send adapter in several ways depending on whether you control the source code for the adapter.  
  
### Send-Side Throttling Improves Performance  
 If you control the source code for the adapter, you can determine from heuristics the maximum number of messages that you want to have in the queue to send at any time. When the Messaging Engine calls the `TransmitMessage` method and passes the send adapter a new message, you can choose to either block the thread or check to see if the number of messages in the queue is larger than the maximum value you determined previously. If the maximum number of messages has been exceeded, you can use the `Resubmit` method to resubmit the message to the Messaging Engine. Note that if the adapter is synchronous, the message would already be blocked.  
  
 If you do not control the source code for the adapter, you can change the number of queued messages by changing the **Highwatermark** value in the Adm_serviceclass table in the BizTalk Management database. The maximum value for the **Highwatermark** property is 200. You can also change the value for the **Lowwatermark** property to a smaller value.  
  
 Remember that the value of the **Highwatermark** property for asynchronous adapters accounts for the number of messages that the Messaging Engine has given to the adapter. The Messaging Engine passes them to the adapter through the `TransmitMessage` method, These messages can be still outstanding in their transmission—for example, if the adapter has not made a corresponding call to the `DeleteMessage`, `Resubmit`, `MoveToNextTransport`, or [Microsoft.BizTalk.TransportProxy.Interop.BatchOperationType.MoveToSuspendQ](http://msdn.microsoft.com/library/microsoft.biztalk.transportproxy.interop.batchoperationtype.aspx) methods. For synchronous adapters, the **Highwatermark** property only accounts for the number of messages the Messaging Engine has passed to the adapter by using the **TransmitMessage** method because this call processes synchronously, blocking the calling Messaging Engine thread.  
  
 If you are writing a send adapter for a protocol that is inherently slow in nature (such as HTTP, FTP, or two-way SOAP), consider the following:  
  
- Such an adapter might receive messages for transmission from the BizTalk Messaging Engine faster than it can transmit them. This discrepancy causes problems at various levels. The messages under transmission remain in memory and take up the virtual memory, slowing down the entire system.  
  
- The adapter might take up protocol-specific resources. For example, it might open too many concurrent connections to the server, which could disrupt the remote server.  
  
- The adapter might affect other adapters. For example, if too many messages queue up for a particular adapter, the Messaging Engine stops issuing requests to other send adapters in that process.  
  
  A solution is to put the slow and fast adapters in separate BizTalk Hosts and control the number of messages by using the "High Watermark" and "Low Watermark" settings.  
  
### Receive-Side Throttling Improves Performance  
 There are numerous situations in which a receive adapter receives messages faster than the rate at which the rest of the system can process the messages. When such a situation occurs, the MessageBox database becomes backlogged. When this happens, the performance of the whole system drops dramatically.  
  
 If this is happening with your adapter, you can use one of the following techniques to reduce the speed of the receive adapter:  
  
- Reduce the Messaging Engine thread pool size. You can control the number of threads that the Messaging Engine uses to publish messages into the MessageBox. By reducing the number of threads, you reduce the rate at which the receive adapter receives messages into the MessageBox. This setting only needs to be done for the host corresponding to the receive handler for the adapter. You should not set this for the host corresponding to the send handler for the adapter, unless you want to slow down the send adapter as well.  
  
- Reduce the adapter batch size. Most fast receive adapters publish messages to the MessageBox in batches. The size of these batches is usually configurable in the receive location property page. By decreasing the batch size you can decrease the overall throughput of messages coming into the system.  
  
- Change other adapter-specific settings. After you complete the two previous steps, you can try adjusting other adapter parameters to further decrease throughput. Some adapters expose internal parameters that can be used to decrease throughput. For example, the MQSeries adapter has a setting for “Ordered Delivery.” Ordered Delivery specifies that the adapter will publish a batch of messages, wait for it to complete, and then publish the next batch. By enabling this setting, you essentially remove all parallelism from the receive adapter. Conversely, tuning the parameters in the opposite way can be used to increase the receiving rate of a receive adapter.  
  
  An adapter can submit as many batches as required to the transport proxy. When the system is heavily stressed, a call to the **Done** method of the **IBTTransportBatch** interface will block the message until the required resources are released to the system.  
  
## Plan for Asynchronous Receive and Send  
 The BizTalk Server messaging APIs have rich support for asynchronous programming. If you want to write a scalable adapter, plan on using the asynchronous model from the start because the asynchronous model provides better concurrency.  
  
 On the receive side, when an adapter submits a batch of messages to the BizTalk Messaging Engine (by calling **IBTTransportBatch::Done**), the Messaging Engine queues up the work using its internal thread pool and returns immediately. The engine processes the messages on a separate thread, leaving the adapter free to read more messages from its source and submit them without waiting for the previous message processing to complete.  
  
 On the send side, your adapter can be either asynchronous or synchronous. However, if your protocol supports asynchronous operations, you should use this support to write a scalable adapter. For example, File and HTTP send adapters are fully asynchronous and they perform very few blocking/synchronous operations.  
  
 Asynchronous operations ensure that both the Messaging Engine and your adapter will continue to do their respective work in parallel and not wait on each other for normal message processing.  
  
## Use Batching to Improve Performance  
 Batching is the best starting point for writing a scalable adapter. This is true for both send-side and receive-side adapters. Every batch goes through a database transaction within BizTalk Server even if your adapter is nontransactional. Because there is a fixed delay associated with each transaction, you should try to minimize the number of transactions by combining more than one operation into a single batch.  
  
## Do Not Starve the .NET Thread Pool  
 Writing BizTalk adapters is an exercise in writing .NET runtime code; writing .NET runtime code is invariably an exercise in asynchronous programming.  
  
 Starving the .NET thread pool is a risk to all asynchronous programming in .NET, and it is particularly important for the BizTalk adapter programmer to avoid.  
  
 The .NET thread pool is a limited but widely shared resource. It is easy to write code that uses one of the .NET thread pool threads and holds onto it for long time, blocking other work items from being executed.  
  
 Whenever you use **BeginInvoke** or use a timer, you are using a .NET thread pool thread. If you have multiple pieces of work to do (for example copying messages out of MQSeries into BizTalk Server), you should execute one work item (one batch of messages into BizTalk Server) and then requeue in the thread pool if there is more work to do. Never sit in a `while` loop on the thread.  
  
 In concrete terms this means replacing `while` loops with repeated calls to **BeginInvoke**. This simple change can dramatically improve the responsiveness and scale-out ability for the whole implementation.  
  
## Choose the Right Measurement When Limiting Batch Size  
 If you are submitting messages to BizTalk Server in batches, do not limit the batch size based only on the message count. Consider what happens when an adapter has been configured to batch based only on message count: If the batch size is two and the adapter gets four messages of size 4 KB, 8 KB, 1 MB, and 5MB respectively, the first batch will be of size 12 KB, and the second batch will be of size 6 MB.  
  
 Because the BizTalk Messaging Engine processes all messages in a single batch sequentially, the second batch in this example will be processed much more slowly than the first batch. This is effectively reducing throughput. A better way to handle this problem is to batch based on both message count and total bytes in the batch (that is, batch size in bytes). There is no magic number for total bytes. However, in a normal processing scenario, if the batch size exceeds 1 MB, you will start seeing poor concurrency and throughput.  
  
 Generally adapters are message agnostic and they do not know the size of the messages in the production environment. The sizes of the incoming messages are likely to vary significantly. Because of this, always use message count and total bytes to build the batch.