---
description: "Learn more about: Properties for Reliable Messaging with the MSMQ Adapter"
title: "Properties for Reliable Messaging with the MSMQ Adapter"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Properties for Reliable Messaging with the MSMQ Adapter
You can improve the reliability of sending and receiving messages with the MSMQ adapter by the way you configure the MSMQ adapter. This topic discusses using several configuration properties for reliable messaging.  
  
## Running MSMQ Adapter Handlers Within a Clustered BizTalk Host  
 One approach to high availability is to run adapter handlers in multiple host instances on different BizTalk servers simultaneously. This approach is not recommended for the MSMQ adapter handlers, because MSMQ does not support remote transacted reads and because the MSMQ send handler maintains a dependency on the locally running instance of the MSMQ service. To provide high availability for the MSMQ send and receive handlers it is recommended that you run the MSMQ adapter handlers in a clustered instance of a BizTalk Host. For more information, see [Considerations for Running Adapter Handlers within a Clustered Host](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md).  
  
## Queue Failure and the Dead Letter Queue  
 After successfully sending a message, there is no error for subsequent messages if the receiving queue is disabled or deleted. This situation could cause loss of messages.  
  
 Setting the **Use Dead Letter Queue** configuration property to **True** prevents you from losing messages. When the property is `True` (the default), messages that the queue does not receive go into the dead letter queue.  
  
## Impersonation and Remote Queues  
 You also have to set the **Use Dead Letter Queue** configuration property to **True** when you use remote queues. If the adapter for MSMQ impersonates a user without permission to use the remote queue, the message could be lost.  
  
 When the property is **True** and the impersonated user does not have permission to use the remote queue, the message goes to the dead letter queue on either the local or remote computer. In a transactional send, the message goes to the dead letter queue on the local computer. In a non-transactional send, the message goes to the dead letter queue on the remote computer.  
  
## Recoverable and Use Journal Queue Properties  
 Both the **Recoverable** and **Use Journal Queue** properties save copies of sent messages. For more information about these properties, see [How to Configure an MSMQ Receive Location](../core/how-to-configure-an-msmq-receive-location.md) and [How to Configure an MSMQ Send Port](../core/how-to-configure-an-msmq-send-port.md).  
  
## See Also  
 [Reliable Messaging with the MSMQ Adapter](../core/reliable-messaging-with-the-msmq-adapter.md)   
 [Considerations for Running Adapter Handlers within a Clustered Host](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)
