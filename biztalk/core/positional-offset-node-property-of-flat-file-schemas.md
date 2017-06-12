---
title: "Positional Offset (Node Property of Flat File Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Positional Offset property [Flat File schemas]"
ms.assetid: 1ad10153-01e4-411b-a54c-5c6decc3a6a3
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Positional Offset (Node Property of Flat File Schemas)
Use the **Positional Offset** property to configure the starting offset of the field relative to the previous sibling or delimiter.  
  
## Applies to Nodes of Type  
 [Field Element](../core/field-element-node-properties.md), [Field Attribute](../core/field-attribute-node-properties.md)  
  
## Category  
 Reference  
  
## Allowed Values  
 Either:  
  
-   No value, resulting in no corresponding annotation in the XSD representation of the schema, and specifying that the default value of zero (0) will be used.  
  
-   A non-negative integer, indicating the starting offset, relative to the previous sibling or delimiter, of the corresponding field in instance messages.  
  
## Default Value  
 No value, resulting in no corresponding annotation in the XSD representation of the schema, and specifying that the default value of zero (0) will be used.  
  
## XSD Persistence  
 As the value of the **pos_offset** attribute of:  
  
-   For **Field Element** nodes, the **element/annotation/appinfo/fieldInfo** annotation element.  
  
-   For **Field Attribute** nodes, the **attribute/annotation/appinfo/fieldInfo** annotation element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Field Element** or **Field Attribute** node in BizTalk Editor and you have:  
  
-   Configured the **Flat File Extension** option for the **Schema Editor Extensions** property of the **Schema** node  
  
-   Set the **Structure** property of the containing **Record** node to **Positional**  
  
## See Also  
 [Supplemental Node Properties for Flat File Schemas](../core/supplemental-node-properties-for-flat-file-schemas.md)