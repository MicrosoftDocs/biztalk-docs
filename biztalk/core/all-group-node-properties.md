---
title: "All Group Node Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "all group node properties [schemas]"
  - "schema node types, all groups"
ms.assetid: b030e1b7-2bc5-4204-a541-0dd2cca0d202
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# All Group Node Properties
Use an **All Group** node when all of its child nodes may appear once or not at all, and in any order, in instance messages.  
  
 When you select an **All Group** node in BizTalk Editor, you can examine and set its associated properties in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window. These properties are divided into the following categories:  
  
-   **Advanced.** This category contains properties that correspond to XSD concepts that can be categorized as advanced, such as converting the group definition from local to global.  
  
-   **General.** This category contains properties that correspond to XSD concepts that can be categorized as basic, such as setting the allowed number of occurrences of the element group.  
  
 Many of the properties associated with **All Group** nodes correspond directly to the semantics of XML Schema definition language (XSD) constructs.For links to information about XSD concepts and specifications, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).  
  
 The following table shows the properties associated with **All Group** nodes that are available in all schemas.  
  
|Property name|Category|Description|  
|-------------------|--------------|-----------------|  
|[Group Reference](../core/group-reference-node-property-of-all-schemas.md)|Advanced|Specifies the globally defined group referenced by the selected **All Group** node, or a new name for this group, thereby converting it to a global **All Group** node.|  
|[Max Occurs](../core/max-occurs-node-property-of-all-schemas.md)|General|Specifies the maximum number of times that to the underlying group content of the selected **All Group** node can occur.|  
|[Min Occurs](../core/min-occurs-node-property-of-all-schemas.md)|General|Specifies the minimum number of times that the underlying group content of the selected **All Group** node can occur.|  
|[Namespace](../core/namespace-node-property-of-all-schemas.md)|General|Displays the namespace for the selected **All Group** node.|  
|[Node Name](../core/node-name-node-property-of-all-schemas.md)|General|Displays the name of the selected **All Group** node, as displayed in the schema tree. This name has one of the following forms:<br /><br /> -   \<All> (the default, when the **Group Reference** property has no value).<br />-   \<Group:*X*>, where "*X*" is the value of the **Group Reference** property.|  
|[Order Type](../core/order-type-node-property-of-all-schemas.md)|Advanced|Identifies the selected node as an **All Group** node, and allows it to be converted to a **Sequence Group** or **Choice Group** node.|  
  
## See Also  
 [Sequence Group Node Properties](../core/sequence-group-node-properties.md)   
 [Choice Group Node Properties](../core/choice-group-node-properties.md)   
 [Node Properties - By Node Type](../core/node-properties-by-node-type.md)   
 [Node Properties - Alphabetical Listings](../core/node-properties-alphabetical-listings.md)