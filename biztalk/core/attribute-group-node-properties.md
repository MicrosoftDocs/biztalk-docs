---
title: "Attribute Group Node Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "attribute group node properties [schemas]"
  - "schema node types, attribute groups"
ms.assetid: f7384d51-9a79-4e69-b436-67bb74db8aac
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Attribute Group Node Properties
When you select an **Attribute Group** node in BizTalk Editor, you can examine and set its associated properties in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window. These properties are divided into the following categories:  
  
-   **Advanced.** This category contains properties that correspond to XSD concepts that can be categorized as advanced, such as changing the name by which the group definition is referenced.  
  
-   **General.** This category contains properties that correspond to XSD concepts that can be categorized as basic, such as its namespace and name.  
  
 **Sequence Group**, **Choice Group**, and **All Group** nodes, collectively known as element group nodes, can be either local or global, depending on whether you give their **Group Reference** property a value. Unlike these element group nodes, **Attribute Group** nodes are always global and are given a default value for their **Group Reference** property of the form "\<AttrGroup:attrGroup*N*>", where "N" is a monotonically increasing number, starting at zero (0).  
  
 Further, **Attribute Group** nodes have no structure beyond the set of attributes that they group together for collective use, whereas element group nodes can have very deep structures.  
  
 Many of the properties associated with **Attribute Group** nodes correspond directly to the semantics of XML Schema definition language (XSD) constructs.For links to information about XSD concepts and specifications, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).  
  
 The following table shows the properties associated with **Attribute Group** nodes that are available in all schemas.  
  
|Property name|Category|Description|  
|-------------------|--------------|-----------------|  
|[Group Reference](../core/group-reference-node-property-of-all-schemas.md)|Advanced|Specifies the globally defined group referenced by the selected **Attribute Group** node.|  
|[Namespace](../core/namespace-node-property-of-all-schemas.md)|General|Displays the namespace for the selected **Attribute Group** node.|  
|[Node Name](../core/node-name-node-property-of-all-schemas.md)|General|Displays the name of the selected **Attribute Group** node, as displayed in the schema tree. This name is of the form:<br /><br /> -   \<AttrGroup:*X*>, where "*X*" is the value of the **Group Reference** property.|  
  
## See Also  
 [Node Properties - By Node Type](../core/node-properties-by-node-type.md)   
 [Node Properties - Alphabetical Listings](../core/node-properties-alphabetical-listings.md)