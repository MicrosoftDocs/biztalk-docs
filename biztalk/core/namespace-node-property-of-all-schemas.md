---
title: "Namespace (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Namespace property [schemas]"
ms.assetid: b4a430b0-aeab-463e-af8c-5e9d351a57bd
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Namespace (Node Property of All Schemas)
Use the **Namespace** property to examine and, for **Any Element** and **Any Attribute** nodes, set the namespace for the selected node, if any.  
  
## Applies to Nodes of Type  
 [Record](../core/record-node-properties.md), [Field Element](../core/field-element-node-properties.md), [Field Attribute](../core/field-attribute-node-properties.md), [Sequence Group](../core/sequence-group-node-properties.md), [Choice Group](../core/choice-group-node-properties.md), [All Group](../core/all-group-node-properties.md), [Attribute Group](../core/attribute-group-node-properties.md), [Any Element](../core/any-element-node-properties.md), [Any Attribute](../core/any-attribute-node-properties.md)  
  
## Category  
 General  
  
## Allowed Values  
 Any valid URI.  
  
## Default Value  
 None.  
  
## XSD Persistence  
 As the value of the prefix on the element name from among the imported namespace prefixes, or as the **namespace** attribute of an **any** or **anyAttribute** element.  
  
## Remarks  
 You can examine this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a node of an appropriate type (including a root **Record** node) in BizTalk Editor.  
  
 This property is read-only for all node types other than **Any Element** and **Any Attribute**.  
  
 When the **Namespace** property is blank, it means that the selected node is in the "blank" namespace. For example, when you define a schema with no value set for its **Target Namespace** property, all of the nodes in that schema are in the blank namespace.  
  
 This property represents a standard XSD construct. For additional information about the corresponding XSD construct, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)