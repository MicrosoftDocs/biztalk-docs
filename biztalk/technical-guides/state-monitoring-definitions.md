---
title: "State Monitoring Definitions | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aa2c8247-5e25-4624-9f0d-c7fe621ffba2
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# State Monitoring Definitions
State monitoring helps answer the question of whether a monitored computer is healthy at a given time from the perspective of a particular application. System Center Operations Manager (SCOM) updates the status of different managed entities exposed to the user and presents the status as part of the state monitoring view.  
  
 To understand the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] State Monitoring view, you must understand the concepts behind SCOM state monitoring. The following terminology is used to describe the key components of state monitoring:  
  
- **Role** - A role that a server is performing in an environment as determined by service discovery. For example, the BizTalk run-time role encapsulates the runtime artifacts and instances in BizTalk Server.  
  
- **Component** - A sub-role that is used as part of the health roll-up to measure the overall health of the server role. For example, the BAM alert component is used to generate alerts to indicate the status of overall health.  
  
- **Instance** - A particular computer may host instance(s) of the server role.  
  
  In brief, the following are the important principles of SCOM state monitoring:  
  
- Health of a computer group is derived from the health of the computers that are contained in the computer group.  
  
- The status of the computer shows whether applications (referred as server roles) running on the computer are healthy, and the health is derived from the health of the hosted applications.  
  
- At the application level (server role), the status of the server role is the overall status of all application instances of that server role. For example, health of one or more artifacts like orchestrations, receives locations, receives ports and so on affects the status and overall health of a BizTalk application.  
  
- At the application instance level (server role instance), the health of the application instance is derived from the health of different areas of the application instance (known as components).  
  
- SCOM alerts are associated with the health of a component. Status of a component is set to red, yellow, or green when alerts are triggered to indicate overall health.  
  
- Health of a component contributes to the health of the server role.  
  
  In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]:  
  
- Each BizTalk Server is considered an instance of the BizTalk Server role.  
  
- The BizTalk Server role in a computer will therefore be computed as a result of all events/activities of all the BizTalk Server processes in that computer.  
  
  The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Management Pack provides state monitoring for BizTalk Server artifacts which includes  
  
- Application artifacts such as orchestrations. Messaging components such as receive ports, receive locations, and send ports.  
  
- Deployment artifacts such as servers, host instances, SSO and so on.  
  
  The following table lists the three states that visually represent the health status of all BizTalk Server platform and application level artifacts. This provides the SCOM operator a high-level view of a multi-server deployment in order to focus on important problems quickly.  
  
|Artifacts|Green|Yellow|Red|  
|---------------|-----------|------------|---------|  
|Application level artifacts|Are in a running state.|Less than 70% of the   instances are faulted.|More than 70% of the instances are faulted or have resulted in critical errors.|  
|Deployment level artifacts|Are in a running state.|Not applicable|Are not in a running state or have stopped.|