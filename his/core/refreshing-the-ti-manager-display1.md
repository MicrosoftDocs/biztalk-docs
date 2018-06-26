---
title: "Refreshing the TI Manager Display1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 608199ab-5988-4233-a4d1-7bc05a2d5f56
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Refreshing the TI Manager Display
The contents of TI (Transaction Integrator) Manager are automatically refreshed as new TI-related entries are written to the Windows Registry. For example, TI Manager refreshes if you add a TI component to, or delete one from, a COM+ application. An automatic refresh, however, does not sort the updates that it makes to the display. For example, if you create a new remote environment (RE), the new remote environment is added to the bottom of the RE tree, rather than inserted alphabetically within the tree. You can manually refresh the display to resort its contents. Manually refreshing the display is also the best way to ensure that TI Manager shows current data from the Windows Registry.  
  
 You can refresh the TI Manager display in either of two ways:  
  
- On the **Action** menu, click **Refresh**.  
  
  -or-  
  
- On the MDI toolbar, click **Refresh**.  
  
## See Also  
 [Managing Transaction Integrator with TI Manager](../core/managing-transaction-integrator-with-ti-manager2.md)