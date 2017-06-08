---
title: "Service Instance and Message Instance States | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.admin.servicemessageinstance.properties"
ms.assetid: 2666a27c-e5f7-4ae6-8f12-afa06bba8876
caps.latest.revision: 22
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Service Instance and Message Instance States
Service instance states and message instance states are displayed on the Group Hub page. They convey information about successfully processed messages and instances, failures, and suspensions during a specified time interval. Following is an explanation of each message instance and service instance state.  
  
## Service Instance States  
  
## UIElement List  
  
|Service Instance state value|Description|  
|----------------------------------|-----------------|  
|**Ready to Run**|A service instance has received an activation message, but hasn't started yet. When the number of ready-to-run instances continually increases, the resources to process the workload may be insufficient or unavailable.|  
|**Scheduled**|Scheduled is a ready-to-run sub-state in which a service is ready to process but will commence processing only within a specified window of time (service window). The service window can be specified by the user in the properties dialog box for the port. Outside of that service window, the service is shown as "scheduled."<br /><br /> Note that when you suspend a scheduled instance and then resume it, the instance goes into a dehydrated state.|  
|**Retrying**|A send port instance periodically re-tries to send a message, typically because the destination URI is unavailable. You can set the retry interval and count in the port properties dialog box.|  
|**Dehydrated**|The orchestration instance is idle and not in memory. Dehydrated is essentially the same state as Retrying, but it relates to an orchestration instead of to a message port. A Dehydrated orchestration typically is reactivated when it receives a message.|  
|**Completed with discarded messages**|The service instance was completed, but some messages were not consumed by the instance.|  
|**Suspended, Resumable**|The service instance is suspended. You may be able to resume the service instance by means of an API call or an administrative action. **Important:**  Resuming a messaging instance will do the following: <ul><li>Resume the messaging instance.</li><li>Send the message to the send port.</li><li>The send port delivers the message to the destination; even if the send port is not in a Started state.</li></ul> <br /><br /> Note that when you suspend a scheduled instance and then resume it, the instance goes into a dehydrated state.|  
|**Suspended, Non-resumable**|The service instance is suspended, and cannot be resumed.<br /><br /> Note that when you suspend a scheduled instance and then resume it, the instance goes into a dehydrated state.|  
|**Active**|The service instance is currently in memory.|  
|**In Breakpoint**|The service instance has stopped execution at a pre-set breakpoint. You can make the service instance resume execution through the Orchestration Debugger or by right-clicking the service instance and selecting **Resume**.|  
  
## Message Instance States  
  
## UIElement List  
  
|Message state value|Description|  
|-------------------------|-----------------|  
|**Delivered (not consumed)**|The message has been delivered to the engine, is being processed, and is in memory. It is considered delivered.|  
|**Consumed**|The message has been processed by a service instance. The service that processed holds onto the reference so that it can access the message later. The message is considered delivered. For example, MSMQ messages are in the Consumed state during batched resending of messages. MSMQ can be blocked while it waits for an acknowledgement, and the messages will be flagged as Consumed until the acknowledgement arrives, at which time MSMQ will restart to send messages.|  
|**Suspended, Resumable**|The service instance associated with the message is suspended, and can be resumed. **Important:**  Resuming a messaging instance will do the following: <ul><li>Resume the messaging instance.</li><li>Send the message to the send port.</li><li>The send port delivers the message to the destination; even if the send port is not in a Started state.</li></ul>|  
|**Suspended, Non-resumable**|The service instance associated with the message is suspended, and cannot be resumed.|  
|**Undelivered**|There may be no services available to process the message, or there may be no services running. For example, in an ordered delivery scenario, a message is Undelivered when another message that precedes it is being retried by the ordered delivery send port.|  
|**Undelivered (retrying)**|The message is associated with a send port that is attempting to resend it because the destination URI is unavailable (see "Retrying" service instance, in "Service Instance States," above).|  
|**Undelivered (scheduled)**|The message is waiting to be sent by a send port that has a service window set.|  
  
## See Also  
 [Viewing Tracked Message and Instance Data](../core/viewing-tracked-message-and-instance-data.md)