---
title: "How to Reorder Downstream LUs1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a75a8d60-6f8e-4a1b-8eb4-b2b698bbea90
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Reorder Downstream LUs
An administrator might create a downstream LU called DOWNLU3, and then realize that two additional LUs are needed. After creating the LUs, with the names DOWNLU2 and DOWNLU4, the LUs would be associated with the listed LU numbers.  
  
|LU name|Downstream LU number|  
|-------------|--------------------------|  
|DOWNLU3|2|  
|DOWNLU2|3|  
|DOWNLU4|4|  
  
 To change the downstream numbers so that they match the digits in the LU names, DOWNLU2 could be reordered so that it is placed before DOWNLU3.  
  
|LU name|Downstream LU number|  
|-------------|--------------------------|  
|DOWNLU2|2|  
|DOWNLU3|3|  
|DOWNLU4|4|  
  
### To reorder the numbering of downstream LUs  
  
1. Verify that the server is inactive. If necessary, right-click the server node, and click **Stop**.  
  
2. In the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] console tree, select the downstream connection with which the LUs are associated.  
  
3. Select one or more LUs and pools that you want to move up in the list.  
  
    To select several adjacent items, click the first item you want, hold down SHIFT, and click the last item.  
  
    To select several nonadjacent items, hold down CTRL as you click the items that you want.  
  
4. To move LUs up or down in the list, click the up or down arrow buttons on the Host Integration Server toolbar.  
  
5. To put configuration changes into effect, restart the server.  
  
### To create a downstream pool  
  
1.  Right-click **Pools**, point to **New**, and then click **Downstream LU Pool**.  
  
2.  Type a pool name and, if desired, a comment. This name identifies the pool on SNA Server, not on the host or downstream system.  
  
3.  To add LUs to the new downstream pool, double-click **Connections**, and then double-click the connection that has the LUs you want to work with.  
  
4.  Verify that the **Pools** node is fully expanded, and drag the first LU into the pool.  
  
5.  To add more LUs to the pool, drag each LU from its place in the **Connections** folder to its downstream LU pool.  
  
6.  On the **Action** menu, click **Save**.  
  
> [!NOTE]
>  Downstream LU pools must contain LUs from a single server. Downstream LUs cannot access pooled downstream LUs from multiple servers.  
  
## See Also  
 [Creating and Configuring LUs](../core/creating-and-configuring-lus1.md)