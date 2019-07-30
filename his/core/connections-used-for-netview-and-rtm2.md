---
title: "Connections Used for NetView and RTM2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 670c84f7-d954-46db-ac66-189aca9c1635
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Connections Used for NetView and RTM
[!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] can make use of NetView, a reporting system that runs on an IBM host (mainframe). NetView sends alerts between the host and the PCs that connect to it. Host Integration Server can also receive information from Response Time Monitor (RTM), a 3270 and NetView facility that monitors the amount of time it takes for a host to respond during 3270 display sessions.  
  
 To send link alerts, link statistics, and application-generated alerts to the NetView program at the host, you must specify the connection on which the alerts will be sent. See the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] online Help for information about specifying the connection.  
  
 RTM data and NetView alerts sent to the host by 3270 users are not necessarily sent via the NetView connection. RTM data is sent on the connection for the session to which it refers, while 3270 user alerts are sent on the connection for the currently selected 3270 session.  
  
 For information about configuring SNA Management to work with NetView and information about configuring the NVAlert service, see [Network Integration User's Guide](../core/network-integration-user-s-guide2.md).  
  
## See Also  
 [Network Management with NetView](../core/network-management-with-netview1.md)