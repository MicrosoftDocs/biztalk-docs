---
title: "Zombies in BizTalk Server | Microsoft Docs"
description: Common causes of zombie messages in BizTalk Server
ms.custom: ""
ms.date: "03/23/2016"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0c684891-e984-442f-b5fd-de5f7cf32b44
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Zombies in BizTalk Server

## What is a zombie?  
  
-   A zombie message is a message that was routed to a running orchestration from the messagebox and was "in flight" when the orchestration ended. An "in flight" message is a message that has been routed to a service instance and so is in a messagebox queue destined for the service instance. Since the message can no longer be consumed by the subscribing orchestration instance, the message is suspended and marked with a ServiceInstance/State value of "Suspended (Non-resumable)".  
  
-   A zombie service instance is an instance of an orchestration which has completed while a message that was routed to the orchestration instance from the messagebox was still "in flight". Since the orchestration instance has ended, it cannot consume the "in flight" messages and so is suspended and marked with a ServiceInstance/State value of "Suspended (Non-resumable)".  
  
## Typical causes
The occurrence of zombies typically falls into one of the following categories:  
  
1. **Terminate control messages** – The orchestration engine allows the use of control messages to cancel all currently running work in a specific orchestration instance. Since the control message immediately halts the running orchestration, zombie instances are not unexpected. A number of Human Workflow related designs tend to use this mechanism as well as some other designs.  
  
2. **Parallel listen receives** – In this scenario the service instance waits for 1 of n messages and when it receives certain messages it does some work and terminates. If messages are received on a parallel branch just as the service instance is terminating, zombies are created.  
  
3. **Sequential convoys with non-deterministic endpoints** – In this scenario, a master orchestration schedule is designed to handle all messages of a certain type in order to meet some type of system design requirement. These design requirements may include ordered delivery, resource dispenser, and batching. For this scenario, the tendency is to define a while loop surrounding a listen with one branch having a receive and the other having a delay shape followed by some construct which sets some variable to indicate that the while loop should stop. This is non-deterministic since the delay could be triggered, but a message could still be delivered. Non-deterministic endpoints like this are prone to generating zombies.  
  
   When a zombie service instance is suspended,  the following error message is generated:  
  
`0xC0C01B4C The instance completed without consuming all of its messages. The instance and its unconsumed messages have been suspended.`  
  
 You can use the [BizTalk Terminator](https://www.microsoft.com/download/details.aspx?id=2846) to help remove zombies.  
  
## See Also  
 **Removing Suspended Service Instances** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]