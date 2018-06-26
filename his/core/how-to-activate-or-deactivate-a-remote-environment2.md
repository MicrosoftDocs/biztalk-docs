---
title: "How to Activate or Deactivate a Remote Environment2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2e5306a5-6393-4307-b66e-b3096b8838e0
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Activate or Deactivate a Remote Environment
When a region on a mainframe fails or is taken offline for administrative maintenance, any method invocation for components associated with the remote environment (RE) that describes that region will fail. Therefore, when a mainframe region is unavailable, you should deactivate the RE that is supported by that region. You can then temporarily move the affected Transaction Integrator (TI) components to another RE (for example, a back-up region for the offline one) so that your TI applications can continue to run. When the mainframe region is restored, you can once again activate the RE for that region. Deactivating an RE for an offline region on a mainframe also reduces the number of error messages that are sent to the Windows Event Log.  
  
 You can check the status of REs by clicking the Remote Environments folder in the TI Manager console tree. The details pane shows icons for all the remote environments contained in the folder. These icons indicate whether a remote environment is active or inactive.  
  
> [!NOTE]
>  If a transaction is in progress at the time that the region on the mainframe is taken offline, the transaction finishes. However, subsequent method invocations will fail.  
  
 **To activate or deactivate a Remote Environment**  
  
 Use one of the following methods to activate or deactivate an RE:  
  
- Start TI Manager, right-click the remote environment (RE) for the mainframe region that you want to activate or deactivate, and click **Activate** or **Deactivate**.  
  
   -or-  
  
- Start TI Manager, click the remote environment (RE) for the mainframe region that you want to activate or deactivate, and then click the green arrow on the tool bar to activate an inactive RE, or click the red arrow to deactivate an active RE.  
  
  If you click the Remote Environments folder in the console tree, the details pane lists all of the REs and indicates the current state of each RE.  
  
## See Also  
 [Creating and Managing Remote Environments with TI Manager](../core/creating-and-managing-remote-environments-with-ti-manager1.md)   
 [Creating and Managing TI Components](../core/creating-and-managing-ti-components2.md)   
 [Getting Started with TI](../core/getting-started-with-ti1.md)