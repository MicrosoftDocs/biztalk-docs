---
title: "Wrap Character (Node Property of Flat File Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Wrap Character property [Flat File schemas]"
ms.assetid: 7a3aa9f6-cc7c-4837-90d1-66ee52361435
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Wrap Character (Node Property of Flat File Schemas)
Use the **Wrap Character** property to configure, on a per-field basis, the character used to wrap one or more characters so that they will be interpreted as simple data, rather than as having the special meaning they have otherwise been assigned.  
  
## Applies to Nodes of Type  
 [Field Element](../core/field-element-node-properties.md), [Field Attribute](../core/field-attribute-node-properties.md)  
  
## Category  
 Flat File  
  
## Allowed Values  
 Either:  
  
-   No value, resulting in no corresponding annotation in the XSD representation of the schema, and specifying that there is no wrap character defined for the selected **Field Element** or **Field Attribute** node. This value is only allowed when the [Wrap Character Type](../core/wrap-character-type-node-property-of-flat-file-schemas.md) property is set to **None**.  
  
-   Any of the predefined character choices in the drop-down list.  
  
-   Any other single character entered in the format indicated by your choice for the **Wrap Character Type** property.  
  
## Default Value  
 No value, resulting in no corresponding annotation in the XSD representation of the schema.  
  
## XSD Persistence  
 As the value of the **wrap_char** attribute of:  
  
-   For **Field Element** nodes, the **element/annotation/appinfo/fieldInfo** annotation element.  
  
-   For **Field Attribute** nodes, the **attribute/annotation/appinfo/fieldInfo** annotation element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Field Element** or **Field Attribute** node in BizTalk Editor and you have:  
  
-   Configured the **Flat File Extension** option for the **Schema Editor Extensions** property of the **Schema** node  
  
-   Set the **Structure** property of the containing **Record** node to **Delimited**  
  
 You must configure the **Wrap Character Type** property as **Character** or **Hexadecimal** before you can configure this property.  
  
## See Also  
 [Supplemental Node Properties for Flat File Schemas](../core/supplemental-node-properties-for-flat-file-schemas.md)   
 [Default Wrap Character (Node Property of Flat File Schemas)](../core/default-wrap-character-node-property-of-flat-file-schemas.md)