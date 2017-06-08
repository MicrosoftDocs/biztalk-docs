---
title: "Instance XPath (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Instance XPath property [schemas], about Instance XPath property"
  - "Instance XPath property [schemas]"
ms.assetid: 46464980-8e70-4c8e-bf71-5b9fa3094807
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Instance XPath (Node Property of All Schemas)
Use the **Instance XPath** property to view the XPath of the element or attribute associated with the selected node in an instance message.  
  
## Applies to Nodes of Type  
 [Record](../core/record-node-properties.md), [Field Element](../core/field-element-node-properties.md), [Field Attribute](../core/field-attribute-node-properties.md), [Any Element](../core/any-element-node-properties.md), [Any Attribute](../core/any-attribute-node-properties.md)  
  
## Category  
 General  
  
## Read-Only Value  
 The XPath of the element or attribute associated with the selected node in an instance message.  
  
## XSD Persistence  
 Implicit in the structure of the XSD.  
  
## Remarks  
 You can examine this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a node of an appropriate type (including a root **Record** node) in BizTalk Editor.  
  
 This property is read-only; however, you can copy this value and paste it to another location.  
  
 When you examine the **Instance XPath** property for **Any Element** and **Any Attribute** nodes, you will see one of the substrings "\<Any>" or "\<AnyAttribute>", respectively, in the property value string. These elements appear in the property value strings as wildcard placeholders in the positions of whatever element(s) or attribute(s), respectively, actually occur in a corresponding instance message. Actual elements named "Any" or attributes named "AnyAttribute" are not likely to occur in instance messages.  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)