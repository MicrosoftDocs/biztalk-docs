---
title: "Maximum Length (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Maximum Length property [schemas]"
ms.assetid: 44fb4f75-fdd9-463d-bba2-6a1e3836981e
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Maximum Length (Node Property of All Schemas)
Use the **Maximum Length** property to specify the maximum length for any instance message data corresponding to the selected **Field Element** or **Field Attribute** node.  
  
## Applies to Nodes of Type  
 [Field Element](../core/field-element-node-properties.md), [Field Attribute](../core/field-attribute-node-properties.md)  
  
## Category  
 Restricted  
  
## Allowed Values  
  
|Value|Description|  
|-----------|-----------------|  
|Positive integer|Specifies the maximum length for data associated with the selected **Field Element** or **Field Attribute** node.|  
|No value|Use this value to clear the property, resulting in no maximum length restrictions for the corresponding data in an instance message. This is the default value.|  
  
## Default Value  
 No value.  
  
## XSD Persistence  
 As the value of the **maxLength** element and its **value** attribute.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Field Element** or **Field Attribute** node in BizTalk Editor and you have set its **Derived By** property to **Restriction**.  
  
 This property represents an XSD concept related to the **simpleType** element and its **restriction** subelement.  
  
 This property applies to unordered base data types, such as **xs:string**, as well as to list-based restriction derivations, specifying the maximum number of space-separated list items that can occur in the corresponding element(s) or attribute(s) in instance messages.  
  
 You can either specify a value for the **Maximum Length** and/or **Minimum Length** properties, or for the **Length** property, but not both.  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)