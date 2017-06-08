---
title: "Wrap Character Type (Node Property of Flat File Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Wrap Character Type property [Flat File schemas]"
ms.assetid: 650d45fd-3afd-44f0-a828-d212168b6d4b
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Wrap Character Type (Node Property of Flat File Schemas)
Use the **Wrap Character Type** property to configure, on a per-field basis, how an alternative wrap character will be expressed in the [Wrap Character](../core/wrap-character-node-property-of-flat-file-schemas.md) property and in the underlying XSD representation, or whether the default wrap character will be used.  
  
## Applies to Nodes of Type  
 [Field Element](../core/field-element-node-properties.md), [Field Attribute](../core/field-attribute-node-properties.md)  
  
## Category  
 Flat File  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**Character**|Indicates that you will provide a wrap character as a character in the **Wrap Character** property, which will be formatted as a character in the XSD representation of the schema.|  
|**Hexadecimal**|Indicates that you will provide the hexadecimal value ("0xNN") of a wrap character in the **Wrap Character** property, which will be formatted as a hexadecimal value in the XSD representation of the schema.|  
|**Default Wrap Character**|Use this value if you want to use the default wrap character for the entire schema, as established by the [Default Wrap Character](../core/default-wrap-character-node-property-of-flat-file-schemas.md) property of the **Schema** node.|  
|**None**|Removes the corresponding annotation in the XSD representation of the schema, if any, specifying that there is no wrap character specified for the selected **Field Element** or **Field Attribute** node.<br /><br /> The [Wrap Character](../core/wrap-character-node-property-of-flat-file-schemas.md) property should not be set to any value when this property is set to **None**.|  
  
## Default Value  
 **None**, resulting in no corresponding annotation in the XSD representation of the schema, and specifying that there is no wrap character specified for the selected **Field Element** or **Field Attribute** node.  
  
## XSD Persistence  
 As the value of the **wrap_char_type** (="char", "hex", or "default") attribute of:  
  
-   For **Field Element** nodes, the **element/annotation/appinfo/fieldInfo** annotation element.  
  
-   For **Field Attribute** nodes, the **attribute/annotation/appinfo/fieldInfo** annotation element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Field Element** or **Field Attribute** node in BizTalk Editor and you have:  
  
-   Configured the **Flat File Extension** option for the **Schema Editor Extensions** property of the **Schema** node  
  
-   Set the **Structure** property of the containing **Record** node to **Delimited**  
  
 If you configure this property with a value of **Character** or **Hexadecimal**, then you can configure the **Wrap Character** property in one of these two formats.  
  
## See Also  
 [Supplemental Node Properties for Flat File Schemas](../core/supplemental-node-properties-for-flat-file-schemas.md)