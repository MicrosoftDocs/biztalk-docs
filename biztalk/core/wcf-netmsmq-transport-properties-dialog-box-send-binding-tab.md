---
title: "WCF-NetMsmq Transport Properties Dialog Box, Send, Binding Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adapters.wcf-netmsmq.transport.send.binding"
helpviewer_keywords: 
  - "WCF-NetMsmq adapters, bindings"
  - "bindings, WCF-NetMsmq adapters"
  - "WCF-NetMsmq adapters, properties"
  - "properties, WCF-NetMsmq adapters"
ms.assetid: 52c6c522-cbb1-44fc-97a1-06e1106dcd76
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF-NetMsmq Transport Properties Dialog Box, Send, Binding Tab
Use the **Binding** tab to configure the binding properties specific to the WCF-NetMsmq send adapter. The WCF-NetMsmq adapter can communicate with a service through binary-encoded messages over the MSMQ transport. The WCF-NetMsmq adapter provides queued communication in a .NET-to-.NET environment.  
  
> [!NOTE]
>  The current version of the WCF-NetMsmq adapter does not support WS-Reliable Messaging.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Open timeout (hh:mmss)**|Specify a time span value that indicates the interval of time provided for a channel open operation to complete. This value should be greater than or equal to **System.TimeSpan.Zero**.<br /><br /> Default value: 00:01:00<br /><br /> Maximum value:  23:59:59|  
|**Send timeout (hh:mmss)**|Specify a time span value that indicates the interval of time provided for a send operation to complete. This value should be greater than or equal to **System.TimeSpan.Zero**.<br /><br /> Default value: 00:01:00<br /><br /> Maximum value:  23:59:59|  
|**Close timeout (hh:mmss)**|Specify a time span value that indicates the interval of time provided for a channel close operation to complete. This value should be greater than or equal to **System.TimeSpan.Zero**.<br /><br /> Default value: 00:01:00<br /><br /> Maximum value:  23:59:59|  
|**Transactional**|Specify the type of the message queue for the destination service: transactional or nontransactional. If this property is selected, each message processed by this send port is delivered only once, and the sender is notified of delivery failures. To send messages through transactional send ports, both the **durable** and **exactlyOnce** binding elements of the service must be set to **true**. If this property is cleared, messages are transferred without delivery assurance.<br /><br /> The default value is selected.|  
|**Message time to live (dd.hh:mm:ss)**|Specify a time span for how long the messages are valid before they are expired and put into the dead-letter queue. This property is set to ensure that time-sensitive messages do not become stale before they are processed by this send port. A message in a queue that is not consumed by this send port within the time interval specified is said to be expired. Expired messages are sent to special queue called the dead letter queue. The location of the dead letter queue is set with the **Dead letter queue** property..<br /><br /> The default is 1.00:00:00|  
|**Use source journal queue**|Specify whether to copies of messages processed by this send port should be stored in the source journal queue.<br /><br /> The default value is cleared.|  
|**Dead letter queue**|Specify the dead-letter queue where messages that have failed to be delivered to the application will be transferred. More information about the messages delivered to the dead letter queue is listed in the following section, "Messages Delivered to the Dead Letter Queue."<br /><br /> Valid values include the following:<br /><br /> -   **None**: No dead letter queue is to be used.<br />-   **System**: Use the system-wide dead letter queue.<br />-   **Custom**: Custom dead letter queue. **Note:**      The custom dead-letter queue is supported only in Message Queuing (MSMQ) 4.0, released with Windows Vista.<br />-   The default is **System**.|  
|**Custom dead letter queue**|Specify the fully qualified URI with the **net.msmq** scheme for the location of the per-application dead letter queue, where messages that have expired or that have failed transfer or delivery are placed. For example, net.msmq://localhost/deadLetterQueueName. The dead letter queue is a queue on the queue manager of the sending application for expired messages that have failed to be delivered. This property is required if the **Dead letter queue** property is set to **Custom**.<br /><br /> More information about the messages delivered to the dead letter queue is listed in the following section, "Messages Delivered to the Dead Letter Queue."<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256<br /><br /> The default is an empty string.|  
  
## Messages Delivered to the Dead Letter Queue  
 The dead-letter queue is a queue managed by the sending application's Queue Manager that stores messages that have failed to be delivered or have expired. The reasons that a message can fail to reach the receiving application include:  
  
-   A transactional message is sent to a nontransactional queue.  
  
-   A nontransactional message is sent to a transactional queue.  
  
-   An unauthenticated message is sent to a queue that accepts only authenticated messages.  
  
-   An unencrypted message is sent to a queue that accepts only encrypted messages.  
  
-   The message expires before the message is delivered to a receiver.  
  
-   The message storage quota of the target computer or the storage quota of the destination queue is exceeded, or there is no available storage space on the target computer when the message arrives.  
  
-   The sender does not have the access rights needed to place the message in the destination queue.  
  
-   The digital signature attached to the message is not valid.  
  
-   An encrypted message cannot be decrypted by the destination queue manager.  
  
-   The destination queue is purged or deleted before the message is retrieved.  
  
    > [!NOTE]
    >  If the **Dead letter queue** property is set to **None**, messages can be lost if target queue service failure occurs. If the **Dead letter queue** property is set to **System**, failed messages are placed in the transactional dead-letter queue or nontransactional dead-letter queue depending on the **Transactional** property.  
  
## See Also  
 [How to Configure a WCF-NetMsmq Send Port](../core/how-to-configure-a-wcf-netmsmq-send-port.md)   
 [Sending and Retrieving Messages within a Transaction](http://go.microsoft.com/fwlink/?LinkId=75752)