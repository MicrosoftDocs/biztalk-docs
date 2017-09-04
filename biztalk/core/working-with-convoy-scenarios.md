---
title: "Working with Convoy Scenarios | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1028ab37-7ead-41a6-a186-53e5344d1a28
caps.latest.revision: 19
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Working with Convoy Scenarios
A *convoy* exists any time that multiple single messages must be related to achieve the required result. There are two main types of convoys: sequential and parallel.  
  
 Under certain conditions, an orchestration instance might receive a group of correlated messages all at the same time. In this situation, a race condition might occur, in which one of the messages in the group must initialize a correlation set in the orchestration instance before the other messages can be correlated to that orchestration instance.  
  
 To ensure that all of the correlated messages are received by the same orchestration instance, BizTalk Server detects the potential for such a race condition and treats these messages as a convoy. At enlistment, the runtime creates a general subscription and identifies it as part of a convoy. After filling this subscription, the messaging engine creates a temporary subscription based on the values in the predefined correlation properties. This temporary subscription is called a *convoy set*. A convoy set is a group of correlation sets that are used in a convoy. All subsequent messages that match the general subscription are evaluated against the convoy set, and those that match are routed to an existing port.  
  
## Using Convoys with Business Processes  
 Consider the following when using convoy processing with a business process:  
  
-   A *correlation set* is a list of properties with specific values that you use to route messages to a specific business process. The correlation set used on a **Receive** shape cannot contain more than three properties used for correlation. This is because these values are identified and stored at the database level, which supports a maximum of three parameters.  
  
-   Parallel and sequential convoys can coexist in the same business process, but they cannot share any correlation sets with each other. This is because each correlation set can belong to only one convoy.  
  
-   BizTalk Server does not support convoy processing when you use the **Start Orchestration** shape to pass an already-initialized correlation set into a new orchestration. This is because convoy sets are handled at the database level, independent of already-running orchestration instances.  
  
-   You cannot use a single **Receive** shape to initialize two or more correlation sets that will be used in separate convoys. For example, suppose that receive r1 initializes correlation sets c1 and c2 for the first convoy, receive r2 follows c1 for the second convoy, and receive r3 follows c2 for the third convoy. The intended convoy sets for the second convoy are c1, r2 and the intended convoy sets for the third convoy are c2, r3, which are all initialized by r1. In this case, the orchestration engine will not treat these as convoys. The example is a valid convoy scenario if both r2 and r3 follow both c1 and c2 (c1, r2, r3 and c2, r2, r3), both follow c1 only (c1, r2, r3), or both follow c2 only (c2, r2, r3).  
  
## Zombies  
 The use of convoys can result in "lost" messages called zombies. When a non-activating receive subscription in a running orchestration matches a message in the MessageBox database, then the MessageBox delivers the message to the orchestration. Because the MessageBox does not know the business logic inside the orchestration, it simply delivers to the orchestration all the messages that match the subscription. If any of these messages are delivered when the orchestration execution flow has passed the receive subscriptions that can consume the messages, then such messages become zombies.  
  
 An example of a situation that creates zombies is a receive inside a loop that iterates 17 times, but 18 messages are delivered that match the receive subscription in the loop. (The MessageBox does not know that the orchestration logic only handles 17 messages.) The 18th message delivered is not consumed by the orchestration because execution flow has already exited the loop. The orchestration is completed with discarded messages (zombies), which are not resumable because the orchestration instance has already completed.  
  
 You can manage zombies by using a Windows Management Instrumentation (WMI) script to query the instances with the "Suspended-NonResumable" state. In addition, the messaging engine writes an error message, "Completed with discarded messages", to the event log.  
  
 Moreover, if you have a sequential convoy with a long-running transactional scope, and the scope has a time-out setting, some orchestration instances may end up in the "Suspended-NonResumable" state. You may also notice that the number of output messages plus the number of "Suspended-NonResumable" instances is less than the number of input messages. This behavior is by design. When a time-out exception happens, the code goes into the exception handler. BizTalk Server calls the exception handler to let it handle the exception, including handling the zombies. You can use a send port in the exception handler to send the zombies to a destination for further review and processing.  
  
 Scenarios other than convoys can also generate zombies. For example, suppose that an orchestration instance is expecting one response message from a business process, and for some reason, it receives two matching subscription response messages. In this case, the second response message becomes a zombie. Another example is when you have a **Listen** shape with a **Receive** shape at one branch and a **Delay** shape at the other branch. If a message arrives at the same time that the time-out occurs, the message becomes a zombie.  
  
 For more information about how to manage zombies, see **Removing Suspended Service Instances** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## Next steps
 [Sequential Convoys](../core/sequential-convoys.md)  
  
 [Parallel Convoys](../core/parallel-convoys.md)  
  
## See Also  
 [Using Correlations in Orchestrations](../core/using-correlations-in-orchestrations.md)