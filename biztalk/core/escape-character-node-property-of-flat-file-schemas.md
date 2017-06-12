---
title: "Escape Character (Node Property of Flat File Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Escape Character property [Flat File schemas]"
ms.assetid: b340d7f6-f299-4c05-a9bb-066baeb9369e
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Escape Character (Node Property of Flat File Schemas)
Use the **Escape Character** property to configure, on a per-record basis, the character used to escape characters that have been given special meanings, allowing their basic meaning to be used.  
  
## Applies to Nodes of Type  
 [Record](../core/record-node-properties.md)  
  
## Category  
 Flat File  
  
## Allowed Values  
 Either:  
  
-   No value, resulting in no corresponding annotation in the XSD representation of the schema and specifying that there is no escape character defined for the currently selected **Record** node.  
  
-   Any of the predefined character choices in the drop-down list.  
  
-   Any other single character entered in the format indicated by your choice for the [Escape Character Type](../core/escape-character-type-node-property-of-flat-file-schemas.md) property.  
  
## Default Value  
 No value, resulting in no annotation being added to the XSD representation of the schema.  
  
## XSD Persistence  
 As the value of the **escape_char** attribute of the **element/annotation/appinfo/recordInfo** annotation element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Record** node (including a root **Record** node) in BizTalk Editor and you have configured the **Flat File Extension** option for the **Schema Editor Extensions** property of the **Schema** node.  
  
 You must configure the **Escape Character Type** property as **Character** or **Hexadecimal** before you can configure this property.  
  
 The escape character is ignored when used with a regular character (non-escape, non-wrap, non-effective delimiters) or as a last character in the message.  
  
## See Also  
 [Supplemental Node Properties for Flat File Schemas](../core/supplemental-node-properties-for-flat-file-schemas.md)   
 [Default Escape Character (Node Property of Flat File Schemas)](../core/default-escape-character-node-property-of-flat-file-schemas.md)