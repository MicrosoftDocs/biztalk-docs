---
title: "Default Escape Character (Node Property of Flat File Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Default Escape Character property [Flat File schemas]"
ms.assetid: dd8beeaf-25c6-4bf5-b16a-3b4554551a0b
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Default Escape Character (Node Property of Flat File Schemas)
Use the **Default Escape Character** property to configure, for the entire schema, the character used to escape characters that have been given special meanings, allowing their basic meaning to be used.  
  
## Applies to Nodes of Type  
 [Schema](../core/schema-node-properties.md)  
  
## Category  
 Flat File  
  
## Allowed Values  
 Either:  
  
-   No value, resulting in no corresponding annotation in the XSD representation of the schema. This value is only allowed when the [Default Escape Character Type](../core/default-escape-character-type-node-property-of-flat-file-schemas.md) property is set to **None**.  
  
-   Any of the predefined character choices in the drop-down list.  
  
-   Any other single character entered in the format indicated by your choice for the **Default Escape Character Type** property.  
  
## Default Value  
 No value, resulting in no annotation being added to the XSD representation of the schema.  
  
## XSD Persistence  
 As the value of the **default_escape_char** attribute of the **schema/annotation/appinfo/schemaInfo** element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select the **Schema** node in BizTalk Editor and you have configured the **Flat File Extension** option for the **Schema Editor Extensions** property of that node.  
  
 You must configure the **Default Escape Character Type** property as **Character** or **Hexadecimal** before you can configure this property.  
  
 You can override the global setting established by this property by setting the [Escape Character](../core/escape-character-node-property-of-flat-file-schemas.md) property for individual **Record** nodes.  
  
 The escape character is ignored when used with a regular character (non-escape, non-wrap, non-effective delimiters) or as a last character in the message.  
  
## See Also  
 [Supplemental Node Properties for Flat File Schemas](../core/supplemental-node-properties-for-flat-file-schemas.md)   
 [Escape Character (Node Property of Flat File Schemas)](../core/escape-character-node-property-of-flat-file-schemas.md)