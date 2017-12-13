---
title: "How to Move a TI Component to Another Remote Environment1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: efb44e38-abba-4dca-9afd-021d9bc9b196
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Move a TI Component to Another Remote Environment
Each Transaction Integrator (TI) component is associated with a specific remote environment (RE), such as CICS Using LU 6.2, when you create the component in HIS Designer. Windows automatically registers a TI component with its appropriate RE when you add the TI component to a COM+ application to create a TI Automation server.  
  
 You can move a component to another RE when, for example, you want to move the component to a different region of a mainframe as your application goes through the cycle of development, testing, and deployment. TI components are designed for a certain type of RE, so you can only move a TI component to another RE of that identical type. However, you can move any component into the Unassigned Components folder to save it. Later, you can associate a component in the Unassigned Components folder with an appropriate RE. Use TI Manager to move TI components from one RE to another or to the Unassigned Components folder.  
  
> [!NOTE]
>  You cannot move components across computer boundaries. For example, if you have two TI Manager consoles open on your computer, one for your computer and the other for a remote computer where TI is also installed, you cannot move a component from a RE on one console into a RE on the other console.  
  
### To move a TI component in TI Manager  
  
1.  Start TI Manager.  
  
2.  Under **Transaction Integrator** in the console tree, find the component that you want to move in either its current RE folder or in the Unassigned Components folder.  
  
3.  Click the component name, and on the **Action** menu, click **Move**.  
  
4.  In the **Move Component** dialog box, click a new RE instance name in the list. (The list only displays those currently defined REs that the selected component can be moved into.)  
  
5.  Click **OK**.  
  
## See Also  
 [Creating and Managing Remote Environments with TI Manager](../core/creating-and-managing-remote-environments-with-ti-manager1.md)   
 [Creating and Managing TI Components](../core/creating-and-managing-ti-components2.md)   
 [Getting Started with TI](../core/getting-started-with-ti1.md)