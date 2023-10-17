---
description: "Learn more about: Transaction Integrator Manager Console"
title: "Transaction Integrator Manager Console1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c04d4748-22d2-41be-b5eb-95dd87f41b44
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Transaction Integrator Manager Console
Transaction Integrator is administered through the Transaction Integrator (TI) Manager management console. Microsoft Management Console (MMC) is a framework for hosting administrative tools called *snap-ins*. In general, a console can contain tools, folders or other containers, Web pages, and other administrative items. These items are displayed in the left pane of the console, or the *console tree*. MMC provides a single user interface for integrating various Microsoft and third-party management tools. You can create custom consoles combining your choice of the various registered snap-ins; for example, you might put the SNA Manager and Transaction Integrator snap-ins together in a single console.  
  
 The TI Manager management console consists of a left pane that displays the console tree and a right pane that displays the properties of the objects in the left pane. The topmost node in the console tree is the **Console Root**, and as you add snap-ins to MMC, they appear under the **Console Root**.  
  
## Console Root Nodes  
 When you first open TI Manager, the console root has three major nodes (or snap-ins):  
  
-   **Transaction Integrator**. This node is the entry point to the TI Manager administrative tool.  
  
-   **Internet Information Services**. This node appears in the console only if Internet Information Services (IIS) is installed on the computer. The **Internet Information Services** node is the entry point to the IIS administrative tool.  
  
### Transaction Integrator Node  
 The **Transaction Integrator** node contains two major subnodes:  
  
-   **Host-Initiated Processing**. You can use this node to view the major elements that are used in a host-initiated processing (HIP) environment.  
  
-   **Windows-Initiated Processing**. You can use this node to view the major elements that are used in a Windows-initiated processing (WIP) environment.  
