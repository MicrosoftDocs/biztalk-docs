---
title: "Character Encoding in the Flat File Disassembler Pipeline Component | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IBaseMessagePart.Charset property"
  - "XMLNorm.SourceCharset property"
  - "pipeline components, Flat File Disassembler"
  - "Flat File Disassembler [pipeline component], character encoding"
ms.assetid: 0dbe24fb-c431-4edf-8aa9-4c040d6a7b32
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Character Encoding in the Flat File Disassembler Pipeline Component
The following algorithm is used by the Flat File Disassembler component to determine which encoding to use for processing an incoming message:  
  
1. If a byte order mark exists in the data, encoding information is determined from it. This encoding information is not preserved by the disassembler (that is, it is not saved to the **XMLNorm.SourceCharset** property).  
  
2. Otherwise, if the **IBaseMessagePart.Charset** property is set, the encoding specified there is used.  
  
3. Otherwise, if the header or document schema contains codepage information, it is used.  
  
4. Otherwise, UTF-8 encoding is used.  
  
   For the preceding cases 2, 3, and 4, the disassembler saves the encoding information on the message context in the **XMLNorm.SourceCharset** property.  
  
## See Also  
 [Flat File Disassembler Pipeline Component](../core/flat-file-disassembler-pipeline-component.md)   
 [How to Configure the Flat File Disassembler Pipeline Component](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md)   
 [Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)