---
title: "Tag Offset (Node Property of Flat File Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Tag Offset property [schemas]"
ms.assetid: 82d7f1a0-5fe4-41d4-958d-81a9d2560f12
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Tag Offset (Node Property of Flat File Schemas)
Use the **Tag Offset** property to specify the starting offset of the tag within the positional record, starting from the beginning of that record. This also means that the tag must fit the positional record and can span more than one field in that record.  
  
## Applies to Nodes of Type  
 [Record](../core/record-node-properties.md)  
  
## Category  
 Flat File  
  
## Allowed Values  
 Non-negative integers.  
  
## Default Value  
 None.  
  
## XSD Persistence  
 As the value of the **tag_offset** attribute of the **element/annotation/appinfo/recordInfo** annotation element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Record** node (including a root **Record** node) in BizTalk Editor and you have:  
  
-   Configured the **Flat File Extension** option for the **Schema Editor Extensions** property of the **Schema** node  
  
-   Set the **Structure** property of the selected **Record** node to **Positional**  
  
-   Set a value for the [Tag Identifier](../core/tag-identifier-node-property-of-flat-file-schemas.md) property of the selected **Record** node  
  
## See Also  
 [Supplemental Node Properties for Flat File Schemas](../core/supplemental-node-properties-for-flat-file-schemas.md)