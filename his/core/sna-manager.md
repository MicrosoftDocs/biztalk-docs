---
title: "SNA Manager1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8c33be37-ef9b-43d6-b327-3d2da7ff120e
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# SNA Manager
SNA Manager provides an interface for configuration and operation of [!INCLUDE[hisHostIntServNoVersion](../core/includes/hishostintservnoversion-md.md)] components. SNA Manager allows flexibility in viewing and managing SNA server subdomains, computers, link services, connections, logical units (LUs), sessions, and users. It integrates the administration of TN3720 service, TN5250 service and Host Print service.  
  
 You can view all [!INCLUDE[hisHostIntServNoVersion](../core/includes/hishostintservnoversion-md.md)] computers in an SNA server subdomain and manage multiple subdomains at the same time. This allows for central configuration and administration of all servers in an enterprise. You can remotely configure and manage Host Integration Server computers across all popular protocols, including TCP/IP and Microsoft Networking.  
  
 SNA Manager can be installed on any computer that is running Windows operating systems enabling management of the entire Host Integration Server network from a single computer. In addition, SNA Manager allows more than one administrator to simultaneously view and manage the same SNA server subdomain.  
  
 SNA Manager provides a hierarchical, tree-like view of an SNA server subdomain and all its resources.  
  
 In the console tree, the subdomain is presented as a hierarchical collection of resources. At the top of the hierarchy is the subdomain itself, which contains Servers, LU Pools, Configured Users, Workstations APPC Modes and CPI-C Symbolic Names. You can view as much of the subdomain detail as needed by opening and closing folders.  
  
 When you click an item in the console tree, the details pane shows resources available to the item. Double-clicking an item that does not contain other objects displays the properties of the item.  
  
 Shortcut menus (available by right-clicking an object) allow selection of the appropriate command for a particular object. For example, if you select a server and right-click, a shortcut menu allows you to stop the service, control all other services, insert new resources, and view and configure the properties.  
  
 SNA Manager lets you administer more than one SNA subdomain by displaying each domain in a separate window with its own hierarchical arrangement of resources.  
  
 SNA Manager also simplifies administrative tasks by providing wizards to step you through many of the more complicated tasks, such as configuring AS/400 connectivity, configuring 3270 display LUs, and creating a range of LUs.  
  
## See Also  
 [IP-DLC Link Service](../Topic/IP-DLC%20Link%20Service1.md)   
 [How to Open a Subdomain](../core/how-to-open-a-subdomain.md)   
 [How to Configure Server Properties](../core/how-to-configure-server-properties.md)   
 [How to Configure SNA Service Properties](../core/how-to-configure-sna-service-properties.md)   
 [Important Configuration Information](../core/important-configuration-information.md)