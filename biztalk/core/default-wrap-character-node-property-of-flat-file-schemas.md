---
title: "Default Wrap Character (Node Property of Flat File Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Default Wrap Character property [Flat File schemas]"
ms.assetid: 27d1b870-fda7-43cc-941f-5122f5a4e5f4
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Default Wrap Character (Node Property of Flat File Schemas)
Use the **Default Wrap Character** property to configure, for the entire schema, the character used to wrap one or more characters so that they will be interpreted as simple data, rather than as having the special meaning they have otherwise been assigned.  
  
## Applies to Nodes of Type  
 [Schema](../core/schema-node-properties.md)  
  
## Category  
 Flat File  
  
## Allowed Values  
 Either:  
  
-   No value, resulting in no corresponding annotation in the XSD representation of the schema. This value is only allowed when the [Default Wrap Character Type](../core/default-wrap-character-type-node-property-of-flat-file-schemas.md) property is set to **None**.  
  
-   Any of the predefined character choices in the drop-down list.  
  
-   Any other single character entered in the format indicated by your choice for the **Default Wrap Character Type** property.  
  
## Default Value  
 No value, resulting in no annotation being added to the XSD representation of the schema.  
  
## XSD Persistence  
 As the value of the **default_wrap_char** attribute of the **schema/annotation/appinfo/schemaInfo** element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select the **Schema** node in BizTalk Editor and you have configured the **Flat File Extension** option for the **Schema Editor Extensions** property of that node.  
  
 You must configure the **Default Wrap Character Type** property as **Character** or **Hexadecimal** before you can configure this property.  
  
 You can override the global setting established by this property by setting the [Wrap Character](../core/wrap-character-node-property-of-flat-file-schemas.md) property for individual **Field Element** and **Field Attribute** nodes.  
  
## See Also  
 [Supplemental Node Properties for Flat File Schemas](../core/supplemental-node-properties-for-flat-file-schemas.md)