---
title: "Repeating Delimiter Type (Node Property of Flat File Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Repeating Delimiter Type property [Flat File schemas]"
ms.assetid: 99852a46-ef7a-48a5-b4ff-d76a24e34c50
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Repeating Delimiter Type (Node Property of Flat File Schemas)
Use the **Repeating Delimiter Type** property to configure, on a per-record basis, how an alternative repeating delimiter string will be expressed in the [Repeating Delimiter](../core/repeating-delimiter-node-property-of-flat-file-schemas.md) property and in the underlying XSD representation, or whether the default repeating delimiter string will be used.  
  
## Applies to Nodes of Type  
 [Record](../core/record-node-properties.md)  
  
## Category  
 Flat File  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**Character**|Indicates that you will provide a repeating delimiter string as characters in the **Repeating Delimiter** property, which will be formatted as characters in the XSD representation of the schema.|  
|**Hexadecimal**|Indicates that you will provide the hexadecimal value ("0xNNNN") of a repeating delimiter string in the **Repeating Delimiter** property, which will be formatted as a hexadecimal value in the XSD representation of the schema.|  
|**Default Repeating Delimiter**|Use this value if you want to use the default repeating delimiter string for the entire schema, as established by the [Default Repeating Delimiter](../core/default-repeating-delimiter-node-property-of-flat-file-schemas.md) property of the **Schema** node.|  
|**None**|Removes the corresponding annotation in the XSD representation of the schema, if any, specifying that there is no repeating delimiter specified for the selected **Record** node.<br /><br /> The [Repeating Delimiter](../core/repeating-delimiter-node-property-of-flat-file-schemas.md) property should not be set to any value when this property is set to **None**.|  
  
## Default Value  
 **None**, resulting in no annotation being added to the XSD representation of the schema, and specifying that there is no repeating delimiter specified for the selected **Record** node.  
  
## XSD Persistence  
 As the value of the **repeating_delimiter_type** (="char", "hex", or "default") attribute of the **element/annotation/appInfo/recordInfo** annotation element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Record** node (including a root **Record** node) in BizTalk Editor and you have:  
  
-   Configured the **Flat File Extension** option for the **Schema Editor Extensions** property of the **Schema** node  
  
-   Set the **Structure** property of the selected **Record** node to **Delimited**  
  
 If you configure this property with a value of **Character** or **Hexadecimal**, then you can configure the **Repeating Delimiter** property in one of these two formats.  
  
## See Also  
 [Supplemental Node Properties for Flat File Schemas](../core/supplemental-node-properties-for-flat-file-schemas.md)