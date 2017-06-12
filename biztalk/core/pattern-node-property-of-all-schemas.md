---
title: "Pattern (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Pattern property [schemas]"
ms.assetid: 86dec810-b972-48d9-8141-3f07e3a3035e
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Pattern (Node Property of All Schemas)
Use the **Pattern** property to limit any data in an instance message corresponding to the selected **Field Element** or **Field Attribute** node to a specific pattern, as specified by one or more regular expressions.  
  
## Applies to Nodes of Type  
 [Field Element](../core/field-element-node-properties.md), [Field Attribute](../core/field-attribute-node-properties.md)  
  
## Category  
 Restricted  
  
## Allowed Values  
 One or more regular expressions that are valid for the data type of the selected **Field Element** or **Field Attribute** node.  
  
## Default Value  
 None.  
  
## XSD Persistence  
 As a **pattern** element and its **value** attribute for each regular expression specified for this property.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Field Element** or **Field Attribute** node in BizTalk Editor and you have set its **Derived By** property to **Restriction**.  
  
 This property represents an XSD concept related to the **simpleType** element and its **restriction** subelement.  
  
 You can create patterns by clicking the ellipsis (**...**) button located to the right of the **Pattern** property value field to open the **Pattern Editor** dialog box. In this dialog box, you can type the regular expressions for your patterns, one per line, into a multi-line edit box labeled **Values**.  
  
 Each of the regular expressions you provide must be valid with respect to the specified data type of the selected **Field Element** or **Field Attribute** node. Some pattern problems are detected immediately; others can result in run-time errors.  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)