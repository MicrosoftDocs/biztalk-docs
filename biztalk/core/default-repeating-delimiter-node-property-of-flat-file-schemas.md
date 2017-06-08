---
title: "Default Repeating Delimiter (Node Property of Flat File Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Default Repeating Delimiter property [Flat File schemas]"
ms.assetid: e58aa100-eebc-449f-8d8f-58803b154205
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Default Repeating Delimiter (Node Property of Flat File Schemas)
Use the **Default Repeating Delimiter** property to configure, for the entire schema, the default string used to delimit repeating fields in instance data.  
  
## Applies to Nodes of Type  
 [Schema](../core/schema-node-properties.md)  
  
## Category  
 Flat File  
  
## Allowed Values  
 Either:  
  
-   No value, resulting in no annotation being added to the XSD representation of the schema. This value is only allowed when the [Default Repeating Delimiter Type](../core/default-repeating-delimiter-type-node-property-of-flat-file-schemas.md) property is set to **None**.  
  
-   Any string of characters entered in the format indicated by your choice for the **Default Repeating Delimiter Type** property.  
  
## Default Value  
 No value, resulting in no annotation being added to the XSD representation of the schema.  
  
## XSD Persistence  
 As the value of the **default_repeating_delimiter** attribute of the **schema/annotation/appinfo/schemaInfo** element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select the **Schema** node in BizTalk Editor and you have configured the **Flat File Extension** option for the **Schema Editor Extensions** property of that node.  
  
 You must configure the **Default Repeating Delimiter Type** property as **Character** or **Hexadecimal** before you can configure this property.  
  
 You can override the global setting established by this property by setting the [Repeating Delimiter](../core/repeating-delimiter-node-property-of-flat-file-schemas.md) property for individual **Record** nodes.  
  
## See Also  
 [Supplemental Node Properties for Flat File Schemas](../core/supplemental-node-properties-for-flat-file-schemas.md)