---
title: "Target Links (Link Property) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Target Links property [schema links]"
ms.assetid: bca1bf68-bc1a-4b48-83f9-cd8e6e5a1bb9
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Target Links (Link Property)
Use the **Target Links** property to determine how the hierarchy below the node that is the target of the link is constructed based on the node that is the source of the link.  
  
## Category  
 Compiler  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**Flatten Links**|Specifies that all source hierarchies are to be flattened to a parent node in the destination schema.|  
|**Match Links Top Down**|Specifies that node hierarchies are to be matched from the top of the source and destinations schemas to the bottom of the source and destination schemas.|  
|**Match Links Bottom Up**|Specifies that node hierarchies are to be matched from the bottom of the source and destination schemas to the top of the source and destination schemas.|  
  
## Default Value  
 **Flatten Links**  
  
## Remarks  
 You can see the effect of this property only when the source and target nodes of the link are at different levels in their respective schemas. This property determines the for-each relationship between the source and target nodes when the data is being copied through this link.  
  
 For more information about node hierarchy matching, see [Node-Hierarchy Level Matching](../core/node-hierarchy-level-matching.md).  
  
## See Also  
 [Link Properties](../core/link-properties.md)