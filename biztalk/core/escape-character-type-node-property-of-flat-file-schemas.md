---
title: "Escape Character Type (Node Property of Flat File Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Escape Character Type property [Flat File schemas]"
ms.assetid: d2aac497-80e9-49f8-a0c7-64e23aa323a4
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Escape Character Type (Node Property of Flat File Schemas)
Use the **Escape Character Type** property to configure, on a per-record basis, how an alternative escape character will be expressed in the [Escape Character](../core/escape-character-node-property-of-flat-file-schemas.md) property and in the underlying XSD representation, or whether the default escape character will be used.  
  
## Applies to Nodes of Type  
 [Record](../core/record-node-properties.md)  
  
## Category  
 Flat File  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**Character**|Indicates that you will provide an escape character as a character in the **Escape Character** property, which will be formatted as a character in the XSD representation of the schema.|  
|**Hexadecimal**|Indicates that you will provide the hexadecimal value ("0xNN") of an escape character in the **Escape Character** property, which will be formatted as a hexadecimal value in the XSD representation of the schema.|  
|**Default Escape Character**|Use this value if you want to use the default escape character for the entire schema, as established by the [Default Escape Character](../core/default-escape-character-node-property-of-flat-file-schemas.md) property of the **Schema** node.|  
|**None**|Removes the corresponding annotation in the XSD representation of the schema, if any, specifying that there is no escape character defined for this **Record** node.<br /><br /> The [Escape Character](../core/escape-character-node-property-of-flat-file-schemas.md) property should not be set to any value when this property is set to **None**.|  
  
## Default Value  
 **None**, resulting in no annotation being added to the XSD representation of the schema.  
  
## XSD Persistence  
 As the value of the **escape_char_type** (="char", "hex", or "default") attribute of the **element/annotation/appinfo/recordInfo** annotation element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Record** node (including a root **Record** node) in BizTalk Editor and you have configured the **Flat File Extension** option for the **Schema Editor Extensions** property of the **Schema** node.  
  
 If you configure this property with a value of **Character** or **Hexadecimal**, then you can configure the **Escape Character** property in one of these two formats.  
  
## See Also  
 [Supplemental Node Properties for Flat File Schemas](../core/supplemental-node-properties-for-flat-file-schemas.md)