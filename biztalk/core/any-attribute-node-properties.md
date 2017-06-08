---
title: "Any Attribute Node Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "any attribute node properties [schemas]"
  - "schema node types, any attribute"
ms.assetid: e23a71b6-68f8-42e1-9415-3d6b71658592
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Any Attribute Node Properties
This node represents the XSD \<anyAttribute> construct.  
  
 When you select an **Any Attribute** node in BizTalk Editor, you can examine and set its associated properties in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window. These properties are all in the **General** category.  
  
 As you develop a schema, you may insert **Any Attribute** nodes to represent a portion of an instance message for which the attributes cannot be anticipated.  
  
 Unlike many other types of nodes, which you can and should rename, the **Any Attribute** node has the fixed node name "\<AnyAttribute>", which you cannot change.  
  
 Many of the properties associated with **Any Attribute** nodes correspond directly to the semantics of XML Schema definition language (XSD) constructs.For links to information about XSD concepts and specifications, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).  
  
> [!NOTE]
>  You can use the **Any Attribute** node with Extensible Markup Language (XML) schemas only. The **Standard** property of the **Schema** node must have a value of **XML** or **Default** for this node type to be allowed without generating a compilation error.  
  
 The following table shows the properties associated with **Any Attribute** nodes that are available in all schemas that represent XML instance messages.  
  
|Property name|Category|Description|  
|-------------------|--------------|-----------------|  
|[Instance XPath](../core/instance-xpath-node-property-of-all-schemas.md)|General|Displays the location within instance messages of the attribute(s) that corresponds to the selected **Any Attribute** node. **Note:**  The XPath value displayed for this property is not technically valid because the actual node name is not known in advance.|  
|[Namespace](../core/namespace-node-property-of-all-schemas.md)|General|Specifies the namespace for the selected **Any Attribute** node.|  
|[Node Name](../core/node-name-node-property-of-all-schemas.md)|General|Indicates that this node is an **Any Attribute** node by displaying the value "\<AnyAttribute>".|  
|[Process Contents](../core/process-contents-node-property-of-all-schemas.md)|General|Specifies the level of validation for data in instance messages that corresponds to the selected **Any Attribute** node.|  
  
## See Also  
 [Any Element Node Properties](../core/any-element-node-properties.md)   
 [Node Properties - By Node Type](../core/node-properties-by-node-type.md)   
 [Node Properties - Alphabetical Listings](../core/node-properties-alphabetical-listings.md)