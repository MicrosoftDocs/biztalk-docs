---
title: "Transaction Integrator (mode) Node2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15376"
ms.assetid: 3e5388eb-a441-40ed-bee6-b655f8e4fe55
caps.latest.revision: 3
robots: noindex,nofollow
---
# Transaction Integrator (mode) Node
Use the **Transaction Integrator** (TI) node to view the basic grouping of elements within the host-initiated processing (HIP) environment and the Windows-initiated processing (WIP) environment. You can also use the **Transaction Integrator** (TI) node to control the operating mode of the TI Manager console.  
  
 All computers that have TI installed are able to share the same physical SQL Server configuration database, and TI Manager allows you to edit the configuration of any computer registered in that database from any TI-enabled computer. In HIP, an administrator could edit database entries such as the host environments, objects, or views that are shared among computers. In WIP, an administrator can only edit local WIP settings.  
  
 Although multiple system administrators using the TI Manager console can concurrently view, start, or stop any application and listener on any TI-enabled computer registered in the configuration database, only one authorized administrator at a time can create or edit the configuration of the TI database.  
  
 As long as the TI Manager is not locked, the administrator can create or edit the following items on any TI-enabled computer:  
  
-   Applications  
  
-   Listeners on an application  
  
-   Local environments  
  
-   Host environments  
  
-   Security policies  
  
-   HIP objects  
  
-   Object views  
  
 The administrator can also create or edit remote environments and WIP objects on the local computer, and can start, stop, or refresh applications and listeners.  
  
## See Also  
 [Host-Initiated Processing Node](../core/host-initiated-processing-node2.md)   
 [Computers Node](../core/computers-node2.md)   
 [Computer Node](../core/computer-node1.md)   
 [Application](../core/application1.md)   
 [Listener](../core/listener2.md)   
 [TI Manager Nodes](../core/ti-manager-nodes2.md)