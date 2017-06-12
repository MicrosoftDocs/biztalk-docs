---
title: "Equivalent Child Node Properties | Microsoft Docs"
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
  - "equivalent node properties [schemas], child nodes"
ms.assetid: b0c313db-da7e-4436-bcca-61be09785bd5
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Equivalent Child Node Properties
Nodes that are child node of an **Equivalent** node are created automatically by BizTalk Editor to show the set of derived complex types and the base complex type from which they are derived. The XML structures specified by any of these types can occur wherever the base complex type is called for in the schema. This yields the same type of polymorphism that is common in many object-oriented programming languages.  
  
 At the location in an instance message where the base complex type is called for by the schema, the structure of the XML can validly conform to that base complex type or to any of the derived complex types, all of which are displayed as child nodes of the **Equivalent** node in the schema.  
  
 In corresponding instance messages, you can use any of the types shown under the **Equivalent** node by specifying the data type explicitly:  
  
```  
<RecordName   
            xmlns:xsi="http://www.w3c.org/2001/XMLSchema-instance">  
  
```  
  
 When you select a node that is the child of an **Equivalent** node in BizTalk Editor, you can examine its read-only properties in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window.  
  
 The following table shows the properties associated with nodes that are child nodes of **Equivalent** nodes.  
  
|Property name|Category|Description|  
|-------------------|--------------|-----------------|  
|[Derivation Type](../core/derivation-type-node-property-of-all-schemas.md)|General|Shows the base complex type or one of the derived complex types.|  
|[Node Name](../core/node-name-node-property-of-all-schemas.md)|General|Shows the name of the base or derived complex type within angle brackets (\<type>).|  
  
## See Also  
 [Equivalent Node Properties](../core/equivalent-node-properties.md)   
 [Node Properties - By Node Type](../core/node-properties-by-node-type.md)   
 [Node Properties - Alphabetical Listings](../core/node-properties-alphabetical-listings.md)