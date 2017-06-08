---
title: "Minimum Length (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Minimum Length property [schemas]"
  - "Minimum Length property [schemas], about Minimum Length property"
ms.assetid: fe25af72-30c4-4f17-afd8-597b269f4935
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Minimum Length (Node Property of All Schemas)
Use the **Minimum Length** property to specify the minimum length for any instance message data corresponding to the selected **Field Element** or **Field Attribute** node.  
  
## Applies to Nodes of Type  
 [Field Element](../core/field-element-node-properties.md), [Field Attribute](../core/field-attribute-node-properties.md)  
  
## Category  
 Restricted  
  
## Allowed Values  
  
|Value|Description|  
|-----------|-----------------|  
|Non-negative integer|Specifies the minimum length for data associated with the selected **Field Element** or **Field Attribute** node.|  
|No value|Use this value to clear the property, resulting in no minimum length restrictions for the corresponding data in an instance message.|  
  
## Default Value  
 No value.  
  
## XSD Persistence  
 As the value of the **minLength** element and its **value** attribute.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Field Element** or **Field Attribute** node in BizTalk Editor and you have set its **Derived Type** property to **Restriction**.  
  
 This property represents an XSD concept related to the **simpleType** element and its **restriction** subelement.  
  
 This property applies to unordered base data types, such as **xs:string**, as well as to list-based restriction derivations, specifying the minimum number of space-separated list items that can occur in the corresponding element(s) or attribute(s) in instance messages.  
  
 You can either specify a value for the **Maximum Length** and/or **Minimum Length** properties, or for the **Length** property, but not both.  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)