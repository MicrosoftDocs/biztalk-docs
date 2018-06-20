---
title: "How to Configure Node Hierarchy Matching | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5302e194-cbc7-4d26-b25b-eb4e38abfe23
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure Node Hierarchy Matching
When you create a link in a map, the BizTalk Mapper automatically creates compiler links to implement the link you have drawn. The **Target Links** property of a link controls how the BizTalk Mapper draws the compiler links. This topic provides information about how to set the target links.  
  
 The **Source Links** property specifies how a value is retrieved from the source node and applied to the destination node. For information about how to set source links, see [How to Set the Source Links Compiler Value](../core/how-to-set-the-source-links-compiler-value.md).  
  
> [!NOTE]
>  This operation requires that BizTalk Mapper is running.  
  
### To set the Target Links property  
  
1. On the map grid page, click a link to which you want to set the target links property.  
  
2. In the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]**Properties** window, set the **Target Links** property to one of the following choices:  
  
   -   **Flatten Links.** The hierarchy in the source record node is flattened to the linked-to-record node in the destination schema.  
  
       > [!NOTE]
       >  By default, the BizTalk Mapper sets the **Target Links** property to **Flatten**.  
  
   -   **Match Links Top Down.** Node matching is performed level-to-level from the top down.  
  
   -   **Match Links Bottom Up.** Node matching is performed level-to-level from the bottom up.  
  
## See Also  
 [Node-Hierarchy Level Matching](../core/node-hierarchy-level-matching.md)   
 [Compiler Directives and Links](../core/compiler-directives-and-links.md)   
 [Using Links to Specify Record and Field Mappings](../core/using-links-to-specify-record-and-field-mappings.md)