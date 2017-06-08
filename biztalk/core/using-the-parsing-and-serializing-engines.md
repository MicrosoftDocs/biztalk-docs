---
title: "Using the Parsing and Serializing Engines | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "parsing engine"
  - "pipeline components [custom], engines"
  - "serialization engine"
  - "pipeline components [custom], assembling"
  - "pipeline components [custom], parsing"
ms.assetid: a9d19703-b074-402a-971a-b2a6cd5d0724
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using the Parsing and Serializing Engines
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] includes a parsing and serializing engine to simplify the process of parsing and serializing flat file documents.  
  
 The parsing engine is a schema-driven framework that can parse many different document formats into XML. In addition, the engine has a well-defined extensibility model to make parsing custom formats even easier.  
  
 For complex parsing, disassemblers are used. In addition to converting the native format to XML, the disassembler can also separate a single document into multiple documents.  
  
 The serializing engine is similar to the parsing engine, except that it works in the opposite direction. Where the parsing engine converts native formats to XML, the serializing engine converts XML to native formats. And just as the parsing engine uses disassemblers, the serializing engine uses assemblers.  
  
 This section discusses how to perform character encoding, parse and serialize based on XML Schema definition language (XSD) schemas, and perform other common tasks using the parsing engine and serializing engine APIs.  
  
## In This Section  
  
-   [Implementing Character Encoding in a Pipeline Component](../core/implementing-character-encoding-in-a-pipeline-component.md)  
  
-   [Using Schemas](../core/using-schemas.md)  
  
-   [Using the Flat File Parsing Engine](../core/using-the-flat-file-parsing-engine.md)  
  
-   [Using the Flat File Serializing Engine](../core/using-the-flat-file-serializing-engine.md)