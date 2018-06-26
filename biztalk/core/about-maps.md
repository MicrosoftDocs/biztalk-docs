---
title: "About Maps | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "file types, maps"
  - "BizTalk Mapper"
  - "maps, file type"
  - "maps, about maps"
  - "BizTalk Mapper, about BizTalk Mapper"
  - "maps"
ms.assetid: 512ef2b7-3d01-4fcf-bb38-de68ec608b07
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# About Maps
Using BizTalk Mapper, you define the relationship between an input and an output schema by using links and functoids. A link defines a direct data copy of a record or field. Links may directly connect to items in the other schema, or they may form connections to functoids. Functoids perform more complex data manipulations, such as:  
  
- Adding the value of two fields in the source schema and copying the result to the destination schema.  
  
- Converting a character to its ASCII format.  
  
- Returning the average of a field in a repeating record and copying the result to a field in the destination schema.  
  
  BizTalk Mapper stores maps in a file with a .btm extension. The file saves design information about the map—the locations of icons representing functoids, the links between schema items and functoids, and other information about the map. When you build or compile the map, BizTalk Mapper converts the information about the map into the corresponding Extensible Language Stylesheet Transformations (XSLT) stylesheet.  
  
> [!NOTE]
>  The [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] compiler has a 16-megabyte limitation on the total size of all strings in a single project. While compiling BizTalk projects, the compiler serializes schemas, maps, and orchestrations for creating the assemblies, and this increases the total size of all strings, which may exceed the limitation. To resolve this issue, you can reorganize your project by putting schemas and/or maps into different Biztalk projects (Typically, under the same solution), such that  the total size of all strings in each project is less than 16 MB.  
  
 The maps that you create can transform or translate data, and they can be specific to a single trading partner or be used with many trading partners. The topics in this section provide an introduction to the concepts involved in mapping schemas. For background information about maps, see [Maps](../core/maps.md).  
  
## In This Section  
  
-   [Links in Maps](../core/links-in-maps.md)  
  
-   [Functoids in Maps](../core/functoids-in-maps.md)  
  
-   [Map Compilation and Testing](../core/map-compilation-and-testing.md)