---
title: "Role Link Shape | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.orch.shape.role.link"
ms.assetid: 6d36cffd-70db-4ed5-a773-1bc33d8c400f
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Role Link Shape
A **Role Link** shape contains placeholders for an implements role and a uses role. It can include one of either, or one of each.  
  
 You can add port types directly to a Role Link shape, using either existing roles or new roles, and existing or new port types.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Identifier** property|Type a unique identifier for this role link.|  
|**Implements Role** property|Click the ellipsis **(…)** button and use the Role Link Wizard to specify the role that this orchestration will play in the role link.|  
|**Initiating Role** property|From the drop-down list, select the role that initiates this role link.|  
|**Ordered Delivery** property|From the drop-down list, select **True** or **False** to specify whether this role link should use ordered delivery.|  
|**Report to Analyst** property|Select **True** if you want to make this shape viewable in the Visual Business Analyst Tool.|  
|**Role Link Type** property|Specify a role link type with the Role Link Wizard.|  
|**Uses Role** property|Click the ellipsis **(…)** button and use the Role Link Wizard to specify the role to which this orchestration will send messages.|  
  
## See Also  
 [How to Use the Role Link Shape](../core/how-to-use-the-role-link-shape.md)