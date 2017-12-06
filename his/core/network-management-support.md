---
title: "Network Management Support2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 012b866f-f93e-4011-875c-e20ce275095d
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Network Management Support
The requirement to manage heterogeneous network environments containing mainframes, midrange systems, and personal computers is a big challenge. This section discusses two mainframe management tools, IBM NetView and Response Time Monitor, which are supported by [!INCLUDE[hisHostIntServNoVersion](../core/includes/hishostintservnoversion-md.md)] and can be used to manage your integrated network.  
  
 [!INCLUDE[hisHostIntServNoVersion](../core/includes/hishostintservnoversion-md.md)] can be managed either from the Host Integration Server computer (and other computers on the LAN) or from the mainframe using NetView. NetView is a centralized network management system that allows you to control SNA network resources, including Host Integration Server.  
  
 Using the IBM Response Time Monitor (RTM) provides additional management of Host Integration Server. RTM measures the length of time it takes for a host to respond to an incoming 3270 end-user request. Working in conjunction with NetView on the mainframe, RTM gathers data from 3270 terminal emulators and sends the information to the host through the NetView connection.  
  
## In This Section  
 [Monitoring Mainframe Response Times](../core/monitoring-mainframe-response-times.md)