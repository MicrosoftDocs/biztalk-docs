---
title: "Status Information2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 24e0d188-21e9-4bf1-9447-3f998692cd16
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Status Information
The [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] SNA Manager provides several types of status messages that can supplement other performance information.  
  
- You can see the status of servers, logical units (LUs), and connections (Active, Inactive, Pending, Stopping, Active [Out of Date], or Error) in the console tree by selecting the server of interest.  
  
- You can view the number of users and the number of sessions by double-clicking the relevant server. This information can be especially useful when combined with data from System Monitor.  
  
- Also on the SNA Manager, you can view the names of active 5250 users being supported by a particular local LU. If there is only one local LU per server, the names will include all users with active 5250 sessions on a particular server.  
  
  For example, click **Servers** in the console tree to view the status of a given SNA subdomain. The status of the servers in that subdomain will appear in the details pane.  
  
## See Also  
 [Host Integration Server Status](../core/host-integration-server-status1.md)