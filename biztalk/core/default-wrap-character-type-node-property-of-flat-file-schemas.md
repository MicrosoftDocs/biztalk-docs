---
title: "Default Wrap Character Type (Node Property of Flat File Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Default Wrap Character Type property [Flat File schemas]"
ms.assetid: ce329474-ac76-41c7-acb0-a9a6405d7578
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Default Wrap Character Type (Node Property of Flat File Schemas)
Use the **Default Wrap Character Type** property to specify, for the entire schema, how an alternative wrap character will be expressed in the [Default Wrap Character](../core/default-wrap-character-node-property-of-flat-file-schemas.md) property and in the underlying XSD representation.  
  
## Applies to Nodes of Type  
 [Schema](../core/schema-node-properties.md)  
  
## Category  
 Flat File  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**Character**|Indicates that you will provide a default wrap character as a character in the **Default Wrap Character** property, which will be formatted as a character in the XSD representation of the schema.|  
|**Hexadecimal**|Indicates that you will provide the hexadecimal value ("0xNN") of a default wrap character in the **Default Wrap Character** property, which will be formatted as a hexadecimal value in the XSD representation of the schema.|  
|**None**|Removes the corresponding annotation in the XSD representation of the schema, if any, specifying that there is no default wrap character for the entire schema. You must explicitly specify an appropriate wrap character for every **Record** node within the schema.<br /><br /> Selecting **Default Wrap Character** for the value of the **Wrap Character** property of any of the **Record** nodes within the schema will result in a compilation error.|  
  
## Default Value  
 **None**, resulting in no annotation being added to the XSD representation of the schema.  
  
## XSD Persistence  
 As the value of the **wrap_char_type** (="char" or "hex") attribute of the **schema/annotation/appinfo/schemaInfo** element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select the **Schema** node in BizTalk Editor and you have configured the **Flat File Extension** option for the **Schema Editor Extensions** property of that node.  
  
 If you configure this property with a value of **Character** or **Hexadecimal**, then you can configure the **Default Wrap Character** property in one of these two formats.  
  
 Setting the **Default Wrap Character Type** property to **None** removes the annotation from the schema. The parser interprets the absence of the annotation as the default case and uses the **Default Wrap Character**, if set. For more information about the parser processing fields, see the `DocumentSchema.ParseFieldInfo Method`.  
  
 You can set the equivalent properties on individual **Field Element** and **Field Attribute** nodes using the [Wrap Character](../core/wrap-character-node-property-of-flat-file-schemas.md) and [Wrap Character Type](../core/wrap-character-type-node-property-of-flat-file-schemas.md) properties. If you set default values for the schema, the default values override values set on individual nodes.  
  
## See Also  
 [Default Wrap Character (Node Property of Flat File Schemas)](../core/default-wrap-character-node-property-of-flat-file-schemas.md)   
 [Supplemental Node Properties for Flat File Schemas](../core/supplemental-node-properties-for-flat-file-schemas.md)   
 [Wrap Character (Node Property of Flat File Schemas)](../core/wrap-character-node-property-of-flat-file-schemas.md)   
 [Wrap Character Type (Node Property of Flat File Schemas)](../core/wrap-character-type-node-property-of-flat-file-schemas.md)