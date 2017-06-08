---
title: "Document Structure Enforcement in the XML Disassembler Pipeline Component | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "XML Disassembler [pipeline component], document structure"
  - "pipeline components, XML Disassembler"
ms.assetid: ac405bf2-f92b-4b45-8256-dd188ec9510a
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Document Structure Enforcement in the XML Disassembler Pipeline Component
If a document or envelope schema is explicitly referenced in the XML Disassembler, the XML Disassembler processes only those documents with message types conforming to the schema. No other documents are processed, regardless of whether a deployed schema is referenced for them.  
  
 The XML Disassembler enforces the specified order of envelope schemas; however, the order of document schemas is not enforced.  
  
## See Also  
 [XML Disassembler Pipeline Component](../core/xml-disassembler-pipeline-component.md)   
 [How to Configure the XML Disassembler Pipeline Component](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)