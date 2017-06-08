---
title: "Default Escape Character Type (Node Property of Flat File Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Default Escape Character Type property [Flat File schemas]"
ms.assetid: 8c553aed-9a8f-4713-8add-b1413116213e
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Default Escape Character Type (Node Property of Flat File Schemas)
Use the **Default Escape Character Type** property to configure, for the entire schema, how an alternative default escape character will be expressed in the [Default Escape Character](../core/default-escape-character-node-property-of-flat-file-schemas.md) property and in the underlying XSD representation.  
  
## Applies to Nodes of Type  
 [Schema](../core/schema-node-properties.md)  
  
## Category  
 Flat File  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**Character**|Indicates that you will provide a default escape character as a character in the **Default Escape Character** property, which will be formatted as a character in the XSD representation of the schema.|  
|**Hexadecimal**|Indicates that you will provide the hexadecimal value ("0xNN") of a default escape character in the **Default Escape Character** property, which will be formatted as a hexadecimal value in the XSD representation of the schema.|  
|**None**|Removes the corresponding annotation in the XSD representation of the schema, if any, specifying that there is no default escape character for the entire schema. You must explicitly specify an appropriate escape character for every **Record** node within the schema.<br /><br /> Selecting **Default Escape Character** for the value of the **Escape Character** property of any of the **Record** nodes within the schema will result in a compilation error.|  
  
## Default Value  
 **None**, resulting in no annotation being added to the XSD representation of the schema.  
  
## XSD Persistence  
 As the value of the **escape_char_type** (="char" or "hex") attribute of the **schema/annotation/appinfo/schemaInfo** element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select the **Schema** node in BizTalk Editor and you have configured the **Flat File Extension** option for the **Schema Editor Extensions** property of that node.  
  
 If you configure this property with a value of **Character** or **Hexadecimal**, then you can configure the **Default Escape Character** property in one of these two formats.  
  
 This value may be overridden for particular **Record** nodes by using the [Escape Character](../core/escape-character-node-property-of-flat-file-schemas.md) and [Escape Character Type](../core/escape-character-type-node-property-of-flat-file-schemas.md) properties.  
  
## See Also  
 [Supplemental Node Properties for Flat File Schemas](../core/supplemental-node-properties-for-flat-file-schemas.md)