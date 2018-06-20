---
title: "Service Instance States | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "service instances, states"
  - "messages, processing"
  - "states, service instances"
ms.assetid: 38189538-72b3-49df-810b-e134362e35ef
caps.latest.revision: 21
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Service Instance States
As a message is processed, the following actions take place:  
  
- In the receive location, the receive adapter—or transport component—receives the message from an external application and submits it to BizTalk Server for processing.  
  
  > [!NOTE]
  >  A message is received by the system in a variety of formats: XML, a flat file, or as an electronic data interchange (EDI) between companies.  
  
- The receive pipeline decrypts, decodes, and disassembles the message.  
  
- The message engine sends the message and its shortcut properties—such as message type and origin—to the MessageBox database.  
  
- When a matching subscription is found, the message is processed according to a set of schemas and maps, and sometimes business rules or policies that reside on the host server.  
  
- After it is processed, the resulting message is persisted (written) to the MessageBox database. The shortcut properties have been modified to indicate where to send the message, for example, which send port to use.  
  
- The shortcut properties of the message are evaluated against the filter expressions defined for the send port, and the MessageBox database delivers the message to the appropriate send port.  
  
- A subscription to a send pipeline and/or send port must be met for the message to be sent. The message is encrypted and transmitted.  
  
  Each process in this cycle generates its own set of events.  
  
  As service instances (receive ports, orchestrations, send ports) process messages moving through BizTalk Server, these service instances can be in one of several states. This section discusses what those states are, and shows examples of states at different times in their lifecycle.  
  
## Service Instance States  
 The following table shows the various possible states of a service instance, with an explanation for each state.  
  
|State|Explanation|  
|-----------|-----------------|  
|**In Breakpoint**|An active orchestration hits a breakpoint, typically one set by a BizTalk Server solutions developer. This state is valid only for orchestrations.|  
|**Ready to run**|A service instance that has been activated but has not yet started running, typically due to temporary unavailability of resources, such as a heavy processing load on the server.|  
|**Active**|Running service instance.|  
|**Dehydrated**|Instance state persists in the MessageBox database and no Windows service is running that instance.|  
|**Completed with discarded messages**|The service instance was completed, but some messages were not consumed by the instance.|  
|**Suspended (resumable)**|Instance suspended, you can resume it. **Important:**  Resuming a messaging instance will do the following: <ul><li>Resume the messaging instance.</li><li>Send the message to the send port.</li><li>The send port delivers the message to the destination; even if the send port is not in a Started state.</li></ul> <br /><br /> Note that when you suspend a scheduled instance and then resume it, the instance goes into a dehydrated state.|  
|**Suspended (not-resumable)**|Instance suspended, but you cannot resume it. You can save the Messages referenced by the instance, and then you can terminate the instance.<br /><br /> Note that when you suspend a scheduled instance and then resume it, the instance goes into a dehydrated state.|  
|**Pending suspend/Pending terminate**|A status, not an independent state. You can combine it with other states.<br /><br /> A control message to suspend or terminate was sent to a service instance, but has not yet been picked up by the instance. Only one pending operation allowed at a time. When an instance with a pending operation becomes dehydrated, you can terminate the instance.|  
  
### Tracked Service Instance States  
 The following table shows the service instance tracking states with an explanation for each state.  
  
|State|Explanation|  
|-----------|-----------------|  
|**Started**|Any service instance that is presently in the MessageBox, for example, in suspended (resumable) or in-breakpoint state, shows up as Started in the BizTalk Tracking database.|  
|**Completed**|The service instance processing has completed successfully.|  
|**Terminated**|The service instance was terminated.|  
  
## Message States  
 The following table shows the states of a message, with an explanation for each state.  
  
|State|Explanation|  
|-----------|-----------------|  
|**Consumed**|The message is being processed by a service instance.|  
|**In Process**|The message has been delivered to the engine and is being processed. It is in memory.|  
|**Queued**|Queued encompasses the Queued (awaiting processing), Queued (scheduled for later delivery), and Queued (waiting to retry) instance states.|  
|**Queued (awaiting processing)**|The message is in an ordered delivery scenario when the preceding message is being retried by the ordered delivery send port.|  
|**Queued (scheduled for later delivery)**|The message is waiting to be sent by a send port that has a service window set.|  
|**Queued (waiting to retry)**|The message is associated with a send port that is attempting to resend it because the destination URI is unavailable.|  
|**Suspended**|Suspended encompasses the Suspended (resumable) and Suspended (not-resumable) instance states.|  
|**Suspended (resumable)**|The service instance associated with the message is suspended, and can be resumed.<br /><br /> Resuming a messaging instance will do the following:<br /><br /> -   Resume the messaging instance.<br />-   Send the message to the send port.<br />-   The send port delivers the message to the destination; even if the send port is not in a Started state.|  
|**Suspended (not-resumable)**|The service instance associated with the message is suspended, and cannot be resumed.|  
  
## Instance States Before and After an Operation  
 The following table shows the states before and after an operation.  
  
> [!NOTE]
>  Starting and ending states show as bold in the left column and top row. The operation shows in the body of the table.  
  
|Starting state|New state after operation is applied|||||||  
|--------------------|------------------------------------------|------|------|------|------|------|------|  
||**In Breakpoint**|**Active**|**Dehydrated**|**Suspended**|**Terminated**|**Pending terminate**|**Pending suspend**|  
|**In Breakpoint**|Attach from debugger|Continue from debugger|Stop Windows Service|||Terminate|Suspend|  
|**In Breakpoint (Dehydrated)**|Attach from debugger|Continue from debugger|Stop Windows Service|Suspend|Terminate|||  
|**Ready to run**||||Suspend|Terminate|||  
|**Scheduled**||Runtime picks up instance because service windows has started||||||  
|**Active**|||Stop Windows Service|||Terminate|Suspend|  
|**Dehydrated**||Runtime picks up instance|Stop Windows Service|Suspend|Terminate|||  
|**Suspended (resumable)**|Resume in breakpoint from debugger|Resume|||Terminate|||  
|**Suspended (not-resumable)**|||||Terminate|||  
|**Terminated with unconsumed messages**|||||Terminate|||  
|**Pending suspend**|Attach can be attempted but should eventually fail||Stop Windows Service|Request processed|Terminate will only work when instance is dehydrated|||  
|**Pending terminate**|Attach can be attempted but should eventually fail||Stop Windows Service, instance dehydrates||Request processed, or instance dehydrated|||  
  
## Instance States During an Operation  
 The following table shows the change of state when the system performs an operation on an instance.  
  
|Starting state|Operation||||||  
|--------------------|---------------|------|------|------|------|------|  
||**Terminate**|**Suspend**|**Resume**|**Resume in breakpoint**|**Continue**|**Attach**|  
|**In Breakpoint**|Terminated|Suspended|||Active|In Breakpoint|  
|**In Breakpoint (Dehydrated)**|Terminated|Suspended|||Active|In Breakpoint|  
|**Ready To run**|Terminated|Suspended|||||  
|**Scheduled**|Terminated|Suspended|||||  
|**Active**|Terminated|Suspended|||||  
|**Dehydrated**|Terminated|Suspended|||||  
|**Suspended (resumable)**|Terminated||Active|In Breakpoint|||  
|**Suspended (not-resumable)**|Terminated||||||  
|**Terminated with unconsumed messages**|Terminated||||||  
|**Pending suspend**|Terminated; will only work when instance is dehydrated|||||Race condition|  
|**Pending terminate**|Terminated; will only work, when instance is dehydrated|||||Race condition|  
  
> [!NOTE]
>  A race condition occurs when the system delivers multiple control messages to the instance, and the order the instance processes them is not guaranteed.  
  
## See Also  
 [Using the Group Hub Page](../core/using-the-group-hub-page.md)