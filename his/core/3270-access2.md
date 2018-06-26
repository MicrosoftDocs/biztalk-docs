---
title: "3270 Access2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8afd9e90-5f6a-4e60-8897-ac72d1a5bc7d
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# 3270 Access
Host Integration Server provides 3270 connectivity through 3270 logical units (LUs). A 3270 LU is known as a dependent LU because it requires a mainframe to function. Each 3270 LU defined within Host Integration Server is configured to use an existing connection to the mainframe system. Each 3270 LU corresponds to a matching LU resource allocated on the host computer, usually specified within VTAM. The 3270 LU definition in Host Integration Server is identified by a number that matches the number of the corresponding LU resource on the mainframe, and by a user-specified name.  
  
 The 3270 LU is further classified by the type of service provided over the connection. Like physical units (PUs) physical units, LU types are designated by numbers. For example, 3270 display data streams are known as LU 2 streams. Within Host Integration Server, a 3270 LU can be configured as one of the following types:  
  
- Display (LU 2)  
  
- Printer (LU 1 or LU 3)  
  
- Application (LUA)  
  
- Downstream  
  
  Once configured, these LUs are accessed from an end-user applications using Host Integration Server client software that is installed on the client workstation. The client software manages communications between a 3270 application (like a terminal emulator) and the Host Integration Server computer. Applications designed for the Host Integration Server client API use the LUs defined within Host Integration Server to establish a communications link from the client personal computer to the mainframe via Host Integration Server.  
  
  The link between the LU definition in Host Integration Server and the host LU resource is called a *session*. Sessions can be permanent and automatically started during initialization, or established on an as-needed basis. Concurrent sessions can share the same physical devices and communications links.  
  
## In This Section  
 [Deployment Strategies (3270)](../core/deployment-strategies-3270-1.md)  
  
## See Also  
 [LU Pools (3270)](../core/lu-pools-3270-1.md)   
 [Assigning LUs to Workstations (3270)](../core/assigning-lus-to-workstations-3270-1.md)   
 [Providing Hot Backup and Load Balancing (3270)](../core/providing-hot-backup-and-load-balancing-3270-1.md)   
 [Planning 3270 Connectivity](../core/planning-3270-connectivity2.md)