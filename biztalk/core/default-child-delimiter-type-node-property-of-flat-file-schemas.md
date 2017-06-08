---
title: "Default Child Delimiter Type (Node Property of Flat File Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Default Child Delimiter Type property [Flat File schemas]"
ms.assetid: 9dac5ce2-c9af-4344-86b9-83ef40db3a6e
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Default Child Delimiter Type (Node Property of Flat File Schemas)
Use the **Default Child Delimiter Type** property to configure, for the entire schema, how an alternative default child delimiter string will be expressed in the [Default Child Delimiter](../core/default-child-delimiter-node-property-of-flat-file-schemas.md) property and in the underlying XSD representation.  
  
## Applies to Nodes of Type  
 [Schema](../core/schema-node-properties.md)  
  
## Category  
 Flat File  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**Character**|Indicates that you will provide a default child delimiter string as characters in the **Default Child Delimiter** property, which will be formatted as characters in the XSD representation of the schema.|  
|**Hexadecimal**|Indicates that you will provide the hexadecimal value ("0xNNNN") of a default child delimiter string in the **Default Child Delimiter** property, which will be formatted as a hexadecimal value in the XSD representation of the schema.|  
|**None**|Removes the corresponding annotation in the XSD representation of the schema, if any, specifying that there is no default child delimiter for the entire schema. You must explicitly specify an appropriate child delimiter for every **Record** node within the schema.<br /><br /> Selecting **Default Child Delimiter** for the value of the **Child Delimiter Type** property of any of the **Record** nodes within the schema will result in a compilation error.|  
  
## Default Value  
 **None**, resulting in no annotation being added to the XSD representation of the schema.  
  
## XSD Persistence  
 As the value of the **child_delimiter_type** (="char" or "hex") attribute of the **schema/annotation/appinfo/schemaInfo** element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select the **Schema** node in BizTalk Editor and you have configured the **Flat File Extension** option for the **Schema Editor Extensions** property of that node.  
  
 If you configure this property with a value of **Character** or **Hexadecimal**, then you can configure the **Default Child Delimiter** property in one of these two formats.  
  
## See Also  
 [Supplemental Node Properties for Flat File Schemas](../core/supplemental-node-properties-for-flat-file-schemas.md)