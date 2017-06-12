---
title: "Pad Character (Node Property of Flat File Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Pad Character property [Flat File schemas]"
ms.assetid: 2b0ec639-08f7-4db7-b8b7-ddb495182d57
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Pad Character (Node Property of Flat File Schemas)
Use the **Pad Character** property to configure the pad character to be used in instance messages, on a per-field basis.  
  
## Applies to Nodes of Type  
 [Field Element](../core/field-element-node-properties.md), [Field Attribute](../core/field-attribute-node-properties.md)  
  
## Category  
 Flat File  
  
## Allowed Values  
 Either:  
  
-   No value, resulting in no corresponding annotation in the XSD representation of the schema, and specifying that the default pad character, space (" "), be used.  
  
-   Any of the predefined character choices in the drop-down list.  
  
-   Any other single character entered in the format indicated by your choice for the [Pad Character Type](../core/pad-character-type-node-property-of-flat-file-schemas.md) property.  
  
## Default Value  
 No value, resulting in no annotation being added to the XSD representation of the schema, and specifying that the default pad character, space (" "), be used.  
  
## XSD Persistence  
 As the value of the **pad_char** attribute of:  
  
-   For **Field Element** nodes, the **element/annotation/appinfo/fieldInfo** annotation element.  
  
-   For **Field Attribute** nodes, the **attribute/annotation/appinfo/fieldInfo** annotation element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Field Element** or **Field Attribute** node in BizTalk Editor and you have configured the **Flat File Extension** option for the **Schema Editor Extensions** property of the **Schema** node.  
  
 You must configure the **Pad Character Type** property as **Character** or **Hexadecimal** before you can configure this property.  
  
## See Also  
 [Supplemental Node Properties for Flat File Schemas](../core/supplemental-node-properties-for-flat-file-schemas.md)