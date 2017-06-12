---
title: "Any Element Node Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "any element node properties [schemas]"
  - "schema node types, any element"
ms.assetid: 9ab407dd-e8b2-4dd5-9c65-4cc8b85d0634
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Any Element Node Properties
This node represents the XSD \<any> construct.  
  
 When you select an **Any Element** node in BizTalk Editor, you can examine and set its associated properties in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window. These properties are all in the **General** category.  
  
 As you develop a schema, you may insert **Any Element** nodes to represent a portion of an instance message for which the elements cannot be anticipated.  
  
 Unlike many other types of nodes, which you can and should rename, the **Any Element** node has the fixed node name "\<Any>", which you cannot change.  
  
 Many of the properties associated with **Any Element** nodes correspond directly to the semantics of XML Schema definition language (XSD) constructs.For links to information about XSD concepts and specifications, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).  
  
> [!NOTE]
>  You can use the **Any Element** node with Extensible Markup Language (XML) schemas only. The **Standard** property of the **Schema** node must have a value of **XML** or **Default** for this node type to be allowed without generating a compilation error.  
  
 The following table shows the properties associated with **Any Element** nodes that are available in all schemas that represent XML instance messages.  
  
|Property name|Category|Description|  
|-------------------|--------------|-----------------|  
|[Instance XPath](../core/instance-xpath-node-property-of-all-schemas.md)|General|Displays the location within instance messages of the element that corresponds to the selected **Any Element** node. **Note:**  The XPath value displayed for this property is not technically valid because the actual node name is not known in advance.|  
|[Max Occurs](../core/max-occurs-node-property-of-all-schemas.md)|General|Defines the maximum number of times that the element corresponding to the selected **Any Element** node can occur in an instance message.|  
|[Min Occurs](../core/min-occurs-node-property-of-all-schemas.md)|General|Defines the minimum number of times that the elements corresponding to this **Any Element** node can occur in an instance message.|  
|[Namespace](../core/namespace-node-property-of-all-schemas.md)|General|Specifies the namespace for the selected **Any Element** node.|  
|[Node Name](../core/node-name-node-property-of-all-schemas.md)|General|Indicates that this node is an **Any Element** node by displaying the value "\<Any>".|  
|[Process Contents](../core/process-contents-node-property-of-all-schemas.md)|General|Specifies the level of validation for data in instance messages that corresponds to the selected **Any Element** node.|  
  
## See Also  
 [Any Attribute Node Properties](../core/any-attribute-node-properties.md)   
 [Node Properties - By Node Type](../core/node-properties-by-node-type.md)   
 [Node Properties - Alphabetical Listings](../core/node-properties-alphabetical-listings.md)