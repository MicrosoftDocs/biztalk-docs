---
title: "Compiling Maps | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "maps, compiling"
  - "XSLT, generating"
  - "maps, validating"
  - "BizTalk Mapper, compiling"
  - "BizTalk Mapper, validating"
ms.assetid: 967181d6-22a9-4a76-ae45-3317c0c6321b
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Compiling Maps
When you validate maps, the BizTalk Mapper compiler component generates an Extensible Stylesheet Language Transformations (XSLT) style sheet. This creates a compiled map that transforms an instance message defined by the source schema to an instance message defined by the destination schema. Compiling a map enforces the structural rules and transformations specified in the grid pages.  
  
 Transformations, such as links, are processed in the same order that records and fields appear in the destination schema. For example, when BizTalk Mapper reaches a destination **Record** or **Field** node with a link, BizTalk Mapper compiles the properties of the link. The action might be a simple copy value from a record or field in the source schema, or the action might involve multiple calculations using functoids and multiple records and fields.  
  
 BizTalk Mapper generates warnings in the **Output** window and **Task List** window when the compiler encounters a situation that might yield incorrect output. For example, if a functoid requires one input parameter and has no input parameters, BizTalk Mapper generates a warning in the **Output** window. In general, you should not use a map in a production environment if it is generating warnings.  
  
 A link to the generated XSLT style sheet also appears in the **Output** window when the map compiles correctly.  
  
 BizTalk Server uses the compiled map to perform the translation of an input instance message to an output instance message.  
  
## See Also  
 [Testing Maps](../core/testing-maps.md)   
 [Data Transformation Configuration](../core/data-transformation-configuration.md)   
 [Node-Hierarchy Level Matching](../core/node-hierarchy-level-matching.md)