---
title: "How to Set or View Remote Environment Properties1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6334c79a-17ca-4569-8010-e2ee650ddd89
caps.latest.revision: 3
---
# How to Set or View Remote Environment Properties
Basic information about a remote environment (RE) is displayed on an item's property sheet. Property sheets are available for the following items:  
  
-   The Transaction Integrator (TI) folder  
  
-   An RE of any type  
  
-   Any component associated with an RE  
  
-   Any component present in the Unassigned Components folder  
  
 In addition, Context-sensitive Help is available for all properties.  
  
> [!NOTE]
>  By default, no time-out value is specified when you create REs that use LU 6.2 or TCP/IP protocols. The TI run-time environment waits indefinitely for the mainframe transaction program to return output parameters. While waiting, the TI run-time environment also blocks the calling client application until a response is received. This behavior is typical for APPC applications. To avoid indefinite blocking, you can set a time-out value (in seconds) for REs using LU 6.2 or TCP/IP protocols. You set the value on the LU 6.2 or TCP/IP tab of the RE's properties page.  
  
### To view or set an item's properties  
  
1.  In TI Manager, right-click the item whose properties you want to view or set.  
  
2.  Click **Properties**.  
  
3.  If the property sheet has more than one tab, click the tab that contains the properties you want to set or view.  
  
## See Also  
 [Creating and Managing Remote Environments with TI Manager](../HIS2010/creating-and-managing-remote-environments-with-ti-manager2.md)   
 [Creating and Managing TI Components](../HIS2010/creating-and-managing-ti-components1.md)   
 [Getting Started with TI](../HIS2010/getting-started-with-ti2.md)