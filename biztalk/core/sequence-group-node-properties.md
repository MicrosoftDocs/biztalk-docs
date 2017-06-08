---
title: "Sequence Group Node Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "sequence group node properties [schemas]"
  - "schema node types, sequence groups"
ms.assetid: f9d6a1c2-d85b-416c-b77a-0acc48bc6049
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Sequence Group Node Properties
Use a **Sequence Group** node when all of its child nodes have to occur in instance messages in the exact same order in which they are defined.  
  
 When you select a **Sequence Group** node in BizTalk Editor, you can examine and set its associated properties in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window. These properties are divided into the following categories:  
  
-   **Advanced.** This category contains properties that correspond to XSD concepts that can be categorized as advanced, such as converting the group definition from local to global.  
  
-   **General.** This category contains properties that correspond to XSD concepts that can be categorized as basic, such as setting the allowed number of occurrences of the element group.  
  
 Many of the properties associated with **Sequence Group** nodes correspond directly to the semantics of XML Schema definition language (XSD) constructs.For links to information about XSD concepts and specifications, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).  
  
 The following table shows the properties associated with **Sequence Group** nodes that are available in all schemas.  
  
|Property name|Category|Description|  
|-------------------|--------------|-----------------|  
|[Group Reference](../core/group-reference-node-property-of-all-schemas.md)|Advanced|Specifies the globally defined group referenced by the selected **Sequence Group** node, or a new name for this group, thereby converting it to a global **Sequence Group** node.|  
|[Max Occurs](../core/max-occurs-node-property-of-all-schemas.md)|General|Specifies the maximum number of times that the underlying group content of the selected **Sequence Group** node can occur.|  
|[Min Occurs](../core/min-occurs-node-property-of-all-schemas.md)|General|Specifies the minimum number of times that the underlying group content of the selected **Sequence Group** node can occur.|  
|[Namespace](../core/namespace-node-property-of-all-schemas.md)|General|Displays the namespace for the selected **Sequence Group** node.|  
|[Node Name](../core/node-name-node-property-of-all-schemas.md)|General|Displays the name of the selected **Sequence Group** node, as displayed in the schema tree. This name has one of the following forms:<br /><br /> -   \<Sequence> (the default, when the **Group Reference** property has no value).<br />-   \<Group:*X*>, where "*X*" is the value of the **Group Reference** property.|  
|[Order Type](../core/order-type-node-property-of-all-schemas.md)|Advanced|Identifies the selected node as a **Sequence Group** node, and allows it to be converted to a **Choice Group** node or, in some circumstances, an **All Group** node.|  
  
## See Also  
 [Choice Group Node Properties](../core/choice-group-node-properties.md)   
 [All Group Node Properties](../core/all-group-node-properties.md)   
 [Node Properties - By Node Type](../core/node-properties-by-node-type.md)   
 [Node Properties - Alphabetical Listings](../core/node-properties-alphabetical-listings.md)