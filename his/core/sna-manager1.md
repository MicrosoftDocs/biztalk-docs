---
title: "SNA Manager | Microsoft Docs"
description: Use SNA Manager to open a subdomain, configure the HIS server properties, and configure the SNA service properties for Host Integration Server
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8c33be37-ef9b-43d6-b327-3d2da7ff120e
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SNA Manager

## What is it
SNA Manager provides an interface for configuration and operation of [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] components. SNA Manager allows flexibility in viewing and managing SNA server subdomains, computers, link services, connections, logical units (LUs), sessions, and users. It integrates the administration of TN3720 service, TN5250 service and Host Print service.  
  
 You can view all [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] computers in an SNA server subdomain and manage multiple subdomains at the same time. This allows for central configuration and administration of all servers in an enterprise. You can remotely configure and manage Host Integration Server computers across all popular protocols, including TCP/IP and Microsoft Networking.  
  
 SNA Manager can be installed on any computer that is running Windows operating systems enabling management of the entire Host Integration Server network from a single computer. In addition, SNA Manager allows more than one administrator to simultaneously view and manage the same SNA server subdomain.  
  
 SNA Manager provides a hierarchical, tree-like view of an SNA server subdomain and all its resources.  
  
 In the console tree, the subdomain is presented as a hierarchical collection of resources. At the top of the hierarchy is the subdomain itself, which contains Servers, LU Pools, Configured Users, Workstations APPC Modes and CPI-C Symbolic Names. You can view as much of the subdomain detail as needed by opening and closing folders.  
  
 When you click an item in the console tree, the details pane shows resources available to the item. Double-clicking an item that does not contain other objects displays the properties of the item.  
  
 Shortcut menus (available by right-clicking an object) allow selection of the appropriate command for a particular object. For example, if you select a server and right-click, a shortcut menu allows you to stop the service, control all other services, insert new resources, and view and configure the properties.  
  
 SNA Manager lets you administer more than one SNA subdomain by displaying each domain in a separate window with its own hierarchical arrangement of resources.  
  
 SNA Manager also simplifies administrative tasks by providing wizards to step you through many of the more complicated tasks, such as configuring AS/400 connectivity, configuring 3270 display LUs, and creating a range of LUs.  

## Open a Subdomain
Before you can configure [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] components, open a subdomain. **Start Subdomain** is used to change  local SNA subdomain, remote SNA Subdomain, and Offline Configuration.  

1.  Start SNA Manager.  
  
2.  In SNA Manager, right-click **SNA Manager** (top level), and select **Open Subdomain**. The **Start SNA Manager for** dialog box appears.  
  
3.  Select the appropriate settings for your subdomain, and click **Finish**.  
  
## Configure server properties
Use the **Server Configuration** to change the Server Name, Subdomain Name, Active Directory OU Name, Server Role (Primary or Backup), and the Restart(MngAgent and SnaBase) properties of HIS.   

1.  Start SNA Manager.  
  
2.  In SNA Manager, right-click the server, and select **Properties**.  
  
3.  To change the server name, click **Change** near the top of the **Server Configuration** tab. Note that the server must be offline before you can change the name.  
  
4.  To set the Group Identity (Subdomain name and Active Directory), Server Role (Primary or Backup), or Network Transports (TCP/IP is default), click **Change** near the bottom of the **Server Configuration** tab.  
  
5.  Make the appropriate changes to your configuration, and then click **OK**.  
  
6.  You must save your configuration to keep the properties you set. Right-click the server, and click **Save Configuration**.  
  
## Configure SNA service properties
Use the **SNA Service configuration** to change the Server Comment, Network Name, and Control Point Name SNA service properties. 

1.  Start SNA Manager.  
  
2.  In SNA Manager, right-click **SNA Service**, and select **Properties**.  
  
3.  Make appropriate changes.  
  
4.  Click **OK** when done.  
  
5.  You must save your configuration to keep the properties you set. Right-click the server, and click **Save Configuration**.  

  
## See Also  
 [IP-DLC Link Service](./ip-dlc-link-service2.md)   