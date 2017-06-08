---
title: "Case (Node Property of Flat File Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Case property [Flat File schemas]"
ms.assetid: ea52fb87-d08d-4265-984b-d71123f51724
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Case (Node Property of Flat File Schemas)
Use the **Case** property to specify whether data in instance messages should be converted to all uppercase, converted to all lowercase, or left as is.  
  
## Applies to Nodes of Type  
 [Schema](../core/schema-node-properties.md)  
  
## Category  
 Flat File  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**Uppercase**|Specifies that data in instance messages should be converted to uppercase when it is processed.|  
|**Lowercase**|Specifies that data in instance messages should be converted to lowercase when it is processed.|  
|**(Default)**|Removes the corresponding annotation in the XSD representation of the schema, if any, resulting in no case conversion being performed.|  
  
## Default Value  
 **(Default)**, resulting in no annotation being added to the XSD representation of the schema, and no case conversion being performed.  
  
## XSD Persistence  
 As the value of the **case** (="upper" or "lower") attribute of the **schema/annotation/appinfo/schemaInfo** element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Schema** node in BizTalk Editor and you have configured the **Flat File Extension** option for the **Schema Editor Extensions** property of that node.  
  
## See Also  
 [Supplemental Node Properties for Flat File Schemas](../core/supplemental-node-properties-for-flat-file-schemas.md)