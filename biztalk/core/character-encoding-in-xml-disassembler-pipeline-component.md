---
title: "Character Encoding in XML Disassembler Pipeline Component | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IBaseMessagePart.Charset property"
  - "pipeline components, XML Disassembler"
  - "XML Disassembler [pipeline component], character encoding"
  - "XMLNorm.SourceCharset property"
ms.assetid: 37962bdc-cbcb-4559-9ae8-6c4be49b4822
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Character Encoding in XML Disassembler Pipeline Component
The XML Disassembler uses the following algorithm to determine which encoding to use for processing incoming messages:  
  
1. If a byte order mark exists in the data, encoding information is determined from it.  
  
2. Otherwise, if the **IBaseMessagePart.Charset** property is set, the encoding specified there is used.  
  
3. Otherwise if the XML declaration is present in the XML document, the encoding specified there is used, provided the XML declaration is ANSI.  
  
4. Otherwise, UTF-8 encoding is used.  
  
   For the preceding cases 2, 3, and 4, after the XML Disassembler determines the encoding, it saves it on the message context in **XMLNorm.SourceCharset** property. Messages produced by the XML Disassembler pipeline component always use UTF-8 encoding. For case 1, encoding determined from the byte order mark is not preserved.  
  
## See Also  
 [XML Disassembler Pipeline Component](../core/xml-disassembler-pipeline-component.md)   
 [How to Configure the XML Disassembler Pipeline Component](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)