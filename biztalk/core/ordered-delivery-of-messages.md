---
title: "Ordered Delivery of Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "backing up, message order"
  - "file transport, message order"
  - "Messaging Engine, transports"
  - "messages, performance"
  - "dynamic send ports, message order"
  - "BTS.SuspendAsNonResumable message context property"
  - "performance, message order"
  - "Messaging Engine, performance"
  - "Messaging Engine, message order"
  - "MessageBox database, message order"
  - "messages, sorting"
  - "backing up, backup transports"
  - "adapters, custom receive adapters"
  - "adapters, messages"
  - "customizing, receive adapters"
ms.assetid: 39e0bba6-81f5-4ae0-af92-837b225bc801
caps.latest.revision: 23
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Ordered Delivery of Messages
Ordered message delivery ensures that messages that are published to the MessageBox database in a given order are delivered to each matching subscriber in the same order in which they were published to the message box.  
  
## Configuring Ordered Message Delivery  
 Ordered message delivery can be configured in the following places:  
  
-   **Receive** shape in an orchestration  
  
-   Send port  
  
## Ordered Delivery with Existing Transports  
 The protocols underlying certain transports, such as FILE and HTTP, are not consistent with the notion of ordered delivery. However, even with such transports, if the port bound to the transport is marked for ordered delivery, then BizTalk Server enforces ordered delivery by ensuring that the transport does not get the next outbound message until the current one has been successfully sent. To achieve this, BizTalk Server passes each message to the transport's adapter in a single batch and waits until the adapter has successfully deleted the message from the message box before delivering the next message, in another batch, to the adapter.  
  
### Ordered Delivery for Custom Adapters  
 There are special considerations for custom receive adapters. It you are writing a custom adapter that supports ordered delivery on receive, the adapter should do the following:  
  
- After submitting a batch of messages, your custom receive adapter should wait for the **BatchComplete** callback from BizTalk Server before submitting the next batch. For more details, see [Interfaces for a Batch-Supported Receive Adapter](../core/interfaces-for-a-batch-supported-receive-adapter.md).  
  
- If a message fails in the pipeline, it should be suspended, preferably as nonresumable. Use the **BTS.SuspendAsNonResumable** message context property in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to flag the message appropriately.  
  
> [!NOTE]
>  Message order can be broken if a suspended message is later resumed. If you do not want this behavior, suspend failed messages as nonresumable.  
  
 For more details on building a custom adapter, see [Developing Custom Adapters](../core/developing-custom-adapters.md).  
  
## Conditions for End-to-End Ordered Message Processing  
 To provide end-to-end ordered delivery the following conditions must be met:  
  
- Messages must be received with an adapter that preserves the order of the messages when submitting them to BizTalk Server. In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], examples of such adapters are MSMQ and MQSeries. In addition, HTTP or SOAP adapters can be used to submit messages in order, but in that case the HTTP or SOAP client needs to enforce the order by submitting messages one at a time.  
  
- You must subscribe to these messages with a send port that has the **Ordered Delivery** option set to `True`.  
  
- If an orchestration is used to process the messages, only a single instance of the orchestration should be used, the orchestration should be configured to use a sequential convoy, and the **Ordered Delivery** property of the orchestration's receive port should be set to `True`.  
  
## Restrictions  
 Ordered delivery of messages is not supported for the following:  
  
- Dynamic send ports in [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)] and previous versions

- Dynamic send ports in [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] (and any newer versions) for those adapter types that **don't** support ordered delivery on static send ports
  
- Backup transports  

  
## Interactions  
 When ordered delivery is configured for a send port, be aware of the following interactions with other configured behaviors in BizTalk Server:  
  
-   For the "Stop sending subsequent messages on current message failure" setting on the same send port:  
  
    -   **False.** Only the failed message is suspended (as not resumable) and all subsequent messages continue to be processed. This preserves the ordering of the non-failed messages but can result in gaps in the sequence. For example, if orders 101, 102, and 103 are received and order 102 is suspended, orders 101 and 103 will continue to be processed in order.  
  
    -   **True.** The send port instance is suspended if any of the messages fails processing. This causes all subsequent messages in the ordered set of messages to be suspended. This preserves message order by preventing delivery of subsequent messages before delivery of the failed message.  
  
-   If a solicit-response send port has the "Stop sending subsequent messages on current message failure" property set to `true`, and if recoverable interchange processing is configured for the disassembly stage of the receive pipeline for the response, then the send port does not stop sending messages (that is, the instance is not suspended) if there is a recoverable error in disassembling the response.  
  
-   Before deleting an ordered send port, ensure that there are no instances associated with it. If there are associated instances, you should terminate them before deleting the send port.  
  
## Ordered Delivery to File Transport  
 Messages arrive at the File adapter in sequence. The File adapter may append messages to a single file or write out a sequence of files, with the following results:  
  
-   If message data is appended to a single file, individual messages are appended in order. The ordered delivery option on a send port that uses the FILE adapter only makes sense if the send transport works in append mode  
  
-   If messages are written to individual files, the order is reflected in the file names, which are sequentially named. In this case, for files written by the adapter, file system properties relating to chronology (for example, file creation time or modification time) do not necessarily reflect the message arrival sequence.  
  
## Performance Impact of Ordered Delivery  
 To achieve ordered delivery, BizTalk Server must serialize processing of ordered messages at various points along the message pathway. This works against scale-out techniques, such as the use of multiple host instances for parallel processing of messages. When using ordered delivery, even ports configured to run on multiple host instances run only on a single host instance to ensure ordered delivery. However, in this situation, high availability is still maintained because the failure of a host instance that is processing ordered delivery of messages results in reprocessing of the failed message on another available host instance.  
  
 When Ordered Delivery is enabled, the default **Retry Interval** is 5 minutes. To improve performance, set the Retry Interval to the lowest value, which is 1 minute. The **Retry Interval** property may accept a value of zero (0) but zero (0) is not valid. The **Retry Count** can also be tuned to the number of retries needed. For example, if you know the request should process in <1 minute and the send port destination is always accessible, set both values to 1.  
  
 To change the Retry values, go to [How to Configure Transport Advanced Options for a Send Port](http://go.microsoft.com/fwlink/p/?LinkID=267697).  
  
 For additional information on Ordered Delivery, refer to the following:  
  
 [BizTalk: End-to-End Ordered Message Processing Options](http://social.technet.microsoft.com/wiki/contents/articles/12887.biztalk-end-to-end-ordered-message-processing-options.aspx)  
  
 [BizTalk: Ordered Delivery](http://social.technet.microsoft.com/wiki/contents/articles/6681.biztalk-ordered-delivery.aspx)  
  
## See Also  
 [Ordered Delivery of Messages with the MSMQ Adapter](../core/ordered-delivery-of-messages-with-the-msmq-adapter.md)   
 [Ordered Delivery of Messages with the MQSeries Adapter](../core/ordered-delivery-of-messages-with-the-mqseries-adapter.md)