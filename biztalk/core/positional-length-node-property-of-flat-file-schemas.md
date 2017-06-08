---
title: "Positional Length (Node Property of Flat File Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Positional Length property [Flat File schemas]"
ms.assetid: 8b3131d4-b8b1-4501-ae94-52de93561bac
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Positional Length (Node Property of Flat File Schemas)
Use the **Positional Length** property to configure the field length from the previous sibling or delimiter.  
  
## Applies to Nodes of Type  
 [Field Element](../core/field-element-node-properties.md), [Field Attribute](../core/field-attribute-node-properties.md)  
  
## Category  
 Reference  
  
## Allowed Values  
 A non-negative integer, indicating the length of the corresponding field in instance messages.  
  
## Default Value  
 No value, resulting in no corresponding annotation in the XSD representation of the schema.  
  
## XSD Persistence  
 As the value of the **pos_length** attribute of:  
  
-   For **Field Element** nodes, the **element/annotation/appinfo/fieldInfo** annotation element.  
  
-   For **Field Attribute** nodes, the **attribute/annotation/appinfo/fieldInfo** annotation element.  
  
## Remarks  
 You can examine this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Field Element** or **Field Attribute** node in BizTalk Editor and you have:  
  
-   Configured the **Flat File Extension** option for the **Schema Editor Extensions** property of the **Schema** node  
  
-   Set the **Structure** property of the containing **Record** node to **Positional**  
  
 You must set a value for this property when you have set the **Structure** property of the containing **Record** node to **Positional**.  
  
## See Also  
 [Supplemental Node Properties for Flat File Schemas](../core/supplemental-node-properties-for-flat-file-schemas.md)