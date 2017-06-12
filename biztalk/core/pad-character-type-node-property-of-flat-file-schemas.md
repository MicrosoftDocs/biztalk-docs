---
title: "Pad Character Type (Node Property of Flat File Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Pad Character Type property [Flat File schemas]"
ms.assetid: 4a1df473-ed54-4b49-8171-a6570a6d5f88
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Pad Character Type (Node Property of Flat File Schemas)
Use the **Pad Character Type** property to configure, on a per-field basis, how an alternative pad character will be expressed in the [Pad Character](../core/pad-character-node-property-of-flat-file-schemas.md) property and in the underlying XSD representation, or whether the default pad character will be used.  
  
## Applies to Nodes of Type  
 [Field Element](../core/field-element-node-properties.md), [Field Attribute](../core/field-attribute-node-properties.md)  
  
## Category  
 Flat File  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**Character**|Indicates that you will provide a pad character as a character in the **Pad Character** property, which will be formatted as a character in the XSD representation of the schema.|  
|**Hexadecimal**|Indicates that you will provide the hexadecimal value ("0xNN") of a pad character in the **Decimal Character** property, which will be formatted as a hexadecimal value in the XSD representation of the schema.|  
|**(Default)/ Default Pad Character Type**|Removes the corresponding annotation in the XSD representation of the schema, if any, specifying that the default pad character, space (" "), be used.|  
  
## Default Value  
 **(Default)**, resulting in no annotation being added to the XSD representation of the schema, and specifying that the default pad character, space (" "), be used.  
  
## XSD Persistence  
 As the value of the **pad_char_type** (="char" or "hex") attribute of:  
  
-   For **Field Element** nodes, the **element/annotation/appinfo/fieldInfo** annotation element.  
  
-   For **Field Attribute** nodes, the **attribute/annotation/appinfo/fieldInfo** annotation element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Field Element** or **Field Attribute** node in BizTalk Editor and you have configured the **Flat File Extension** option for the **Schema Editor Extensions** property of the **Schema** node.  
  
 If you configure this property with a value of **Character** or **Hexadecimal**, then you can configure the **Pad Character** property in one of these two formats.  
  
## See Also  
 [Supplemental Node Properties for Flat File Schemas](../core/supplemental-node-properties-for-flat-file-schemas.md)