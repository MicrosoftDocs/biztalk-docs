---
description: "Learn more about: Working with Direct Bound Ports in Orchestrations"
title: "Working with Direct Bound Ports in Orchestrations"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Working with Direct Bound Ports in Orchestrations
There are three types of direct bound ports: MessageBox, self-correlating, and partner orchestration.  
  
 MessageBox direct bound ports allow for publish-subscribe design patterns. Messages sent on a MessageBox direct bound port are published to the MessageBox database, where message recipients pick them up based on subscriptions. Logical receive ports configured as MessageBox direct bound ports get messages directly from the MessageBox database. For activating **Receive** shapes, the MessageBox direct bound receive ports get the messages through subscriptions to the message type and the filter expression. For non-activating **Receive** shapes, the MessageBox direct bound receive ports get the messages through subscriptions to the message type and the correlation set.  
  
 Self-correlating direct bound ports assist you in designing asynchronous inter-orchestration communication. Messages sent to a self-correlating direct bound port are routed to the instance of the orchestration that created the receiving end of the self-correlated direct bound port.  
  
 Partner orchestration direct bound ports provide for inter-orchestration communication. Messages sent on a partner orchestration direct bound port can be sent to an intended recipient orchestration, and messages received on a partner orchestration direct bound port can be received from an intended sender orchestration.  
  
 Although with direct binding, the message appears to go directly from one orchestration to another, in fact any message sent through any type of logical port always travels through the MessageBox database. Moreover, direct bound ports are only logical ports and therefore direct binding is only a design-time configuration feature. A direct bound port cannot be bound to a physical port, and you can only change the direct binding configuration at design time.  
  
## In This Section  
  
-   [How to Use MessageBox Direct Bound Ports](../core/how-to-use-messagebox-direct-bound-ports.md)  
  
-   [How to Use Self-Correlating Direct Bound Ports](../core/how-to-use-self-correlating-direct-bound-ports.md)  
  
-   [How to Use Partner Orchestration Direct Bound Ports](../core/how-to-use-partner-orchestration-direct-bound-ports.md)  
  
## See Also  
 [Port Bindings](../core/port-bindings.md)
