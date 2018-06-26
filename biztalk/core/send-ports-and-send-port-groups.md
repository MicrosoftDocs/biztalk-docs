---
title: "Send Ports and Send Port Groups | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "send ports, states"
  - "send port groups"
  - "send port groups, states"
  - "send ports, about send ports"
  - "send ports"
  - "send port groups, about send port groups"
  - "states, send ports"
ms.assetid: 274bdd27-9098-46a2-8762-8b57bbfc95b8
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Send Ports and Send Port Groups
A *send port* is the location to which Microsoft BizTalk Server sends messages or from which BizTalk Server receives messages. It also provides the technology that BizTalk Server uses to implement the communication action. The name of the port uniquely identifies the location.  
  
 Any time a message is sent to a send port a new instance of a send port service is created. This is called a service instance, also known as a Send Port Instance.  
  
> [!NOTE]
>  There can only be one instance of an In-order delivery send port.  
  
 A *send port group* is a named collection of send ports that BizTalk Server can use to send the same message to multiple destinations in one configuration.  
  
 BizTalk Server can directly route messages from receive locations to a send port, or to a send port group. BizTalk Server sends messages routed to a send port group to all of the send ports in that group.  
  
 Send ports that are members of a send port group process messages in two ways:  
  
-   As a member of the send port group  
  
-   As if BizTalk Server routed the messages to the send port directly  
  
## Send Port and Send Port Group States  
 The BizTalk Administration Console displays send ports and send port groups in one of the following states:  
  
- **Bound**. Using the BizTalk Server Administration Console, an administrator binds the send port or send port group to an orchestration. Before BizTalk Server routes messages to this send port or send port group, the administrator must enlist and start the bound send port or send port group.  
  
- **Started**. The subscription for this send port or send port group exists and is active. When the send port or send port group is in the started state, BizTalk Server delivers messages to the send port or send port group, and the send port or send port group processes them. Before you can start a send port or send port group, an administrator must use the BizTalk Administration Console to enlist the bound send port or send port group.  
  
- **Stopped**. The send port or send port group is not currently running. If you started the send port or send port group and then stopped it, processing continues in the work queue. BizTalk Server sends all new messages routed to a stopped send port or send port group to the suspended queue of the host where the send handler is running.  
  
  The following table shows the actions available from each state, and the result of each.  
  
||Bound|Stopped|Started|  
|------|-----------|-------------|-------------|  
|**Enlist**|Stopped|Not available|Not available|  
|**Start**|Started|Started|Not available|  
|**Stop**|Not available|Not available|Stopped|  
|**Unenlist**|Not available|Bound|Bound|  
  
 The combined state of a send port and the send port group it belongs to determines if the send port or the send port group processes a message or not.  
  
 The following table describes the possible state combinations for send ports and send port groups.  
  
|Message Sent|State of Send Port Group|State of Send Port|Outcome|  
|------------------|------------------------------|------------------------|-------------|  
|Directly to the send port|Any state|Started|Message is processed|  
|Directly to the send port|Any state|Stopped|Message is suspended|  
|To the send port by means of a send port group|Started|Started|Message is processed|  
|To the send port by means of a send port group|Any state|Stopped|Message is suspended|  
|To the send port by means of a send port group|Stopped|Any state|Message is suspended|  
  
## See Also  
 [Artifacts](../core/artifacts.md)