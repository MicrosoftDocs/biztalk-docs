---
title: "Equivalent Node Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "schema node types, equivalent"
  - "equivalent node properties [schemas]"
  - "equivalent node properties [schemas], about equivalent node properties"
ms.assetid: b77dc843-fce6-4397-a133-eabd1b446256
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Equivalent Node Properties
**Equivalent** nodes are created automatically by BizTalk Editor to show how derived complex types can be used instead of the base complex type from which they are derived wherever the base complex type is called for in the schema. This yields the same type of polymorphism that is common in many object-oriented programming languages.  
  
 At the location in an instance message where the base complex type is called for by the schema, the structure of the XML can validly conform to that base complex type or to any of the derived complex types, all of which are displayed as child nodes of the **Equivalent** node in the schema.  
  
 When you select an **Equivalent** node in BizTalk Editor, you can examine its read-only properties in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window.  
  
 The following table shows the properties associated with **Equivalent** node.  
  
|Property name|Category|Description|  
|-------------------|--------------|-----------------|  
|[Base Type](../core/base-type-node-property-of-all-schemas.md)|General|Shows the base complex type upon which the named derivations are based.|  
|[Node Name](../core/node-name-node-property-of-all-schemas.md)|General|Shows that this node is an **Equivalent** node by displaying the value "\<Equivalent>".|  
  
## See Also  
 [Equivalent Child Node Properties](../core/equivalent-child-node-properties.md)   
 [Node Properties - By Node Type](../core/node-properties-by-node-type.md)   
 [Node Properties - Alphabetical Listings](../core/node-properties-alphabetical-listings.md)