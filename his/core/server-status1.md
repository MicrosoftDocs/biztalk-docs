---
title: "Server Status1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cc8fabed-8cdb-4ef5-a542-2f388beb39b7
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Server Status
You can view the status of servers in a given subdomain, including the number of active users, and you can view the properties for a server to gather status information. There are six status types on the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] SNA Manager:  
  
- Active  
  
- Inactive  
  
- Pending  
  
- Stopping  
  
- Active [Out of Date]: Indicates that the Host Integration Server resource needs to be restarted to bring the internal parameters up to date with the latest configuration changes. First, select the affected Host Integration Server resource. Then, on the **Action** menu, click **Stop**, and then click **Start**.  
  
- Error: Indicates that an unexpected condition has made the server inaccessible to the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] SNA Manager.  
  
  You can also see the number of active users, 3270 sessions, Advanced Program-to-Program Communtications (APPC) sessions, and Logical Unit for Applications (LUA) sessions. If the server is active, the number of licensed users and licensed sessions is also shown.  
  
> [!IMPORTANT]
>  If the [Out of Date] message appears on the status bar at the bottom of the SNA Manager (as opposed to in the console tree), then the SNA Manager is out of synchronization with the rest of the SNA subdomain. The SNA Manager is out of date when another server saves the configuration file, so your copy of the file (which resides in RAM memory) is out of sync with the master configuration file. To synchronize your copy of the configuration file, go to the **Action** menu, and click **Refresh**.  
  
## See Also  
 [Host Integration Server Status](../core/host-integration-server-status1.md)