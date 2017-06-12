---
title: "Length (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Length property [schemas]"
ms.assetid: 9494883a-c424-4dc6-bc71-9d2e2514a0e9
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Length (Node Property of All Schemas)
Use the **Length** property to specify a fixed length for the data in instance messages that corresponds to the selected **Field Element** or **Field Attribute** node.  
  
## Applies to Nodes of Type  
 [Field Element](../core/field-element-node-properties.md), [Field Attribute](../core/field-attribute-node-properties.md)  
  
## Category  
 Restricted  
  
## Allowed Values  
 Non-negative integers. A value of zero (0) means that the corresponding element(s) or attributes in instance messages cannot have any data associated with them.  
  
## Default Value  
 None.  
  
## XSD Persistence  
 As the value of the **Length** element and its **value** attribute, within the **restriction** element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Field Element** node in BizTalk Editor and you have set its **Derived Type** property to **Restriction**.  
  
 This property represents a standard XSD concept related to the **simpleType** element and its **restriction** subelement.  
  
 This property applies to unordered base data types, such as **xs:string**, as well as to list-based restriction derivations, specifying the number of space-separated list items that must occur in the corresponding element(s) or attribute(s) in instance messages.  
  
 You can either specify a value for the **Length** property, or for the **Maximum Length** and/or **Minimum Length** properties, but not both.  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)