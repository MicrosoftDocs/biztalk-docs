---
title: "Character Encoding in the Flat File Assembler Pipeline Component | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Flat File Assembler [pipeline component], character encoding"
  - "IBaseMessagePart.Charset property"
  - "pipeline components, Flat File Assembler"
  - "Codepage property"
  - "XMLNorm.SourceCharset property"
  - "XMLNorm.TargetCharset property"
  - "Target Charset property"
ms.assetid: 0cf3c0fd-f036-4190-83ce-9064ef4e823c
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Character Encoding in the Flat File Assembler Pipeline Component
The Flat File Assembler can produce messages in user-specified character encoding. You can specify the character encoding at several levels:  
  
- **Schema.** Set the **codepage** property in the flat file schema for the document.  
  
- **Component.** Set the **Target Charset** component property in Pipeline Designer.  
  
- **Message.** Set the **XMLNorm.TargetCharset** property on the message context.  
  
  The value of the property set on a message context always overrides the one set in Pipeline Designer. Also, the value set in Pipeline Designer always overwrites the value set as a **codepage** property in a flat file document schema.  
  
  The Flat File Assembler uses the following algorithm to determine which encoding to use for an output message:  
  
- If the **XMLNorm.TargetCharset** context property is set, its value is used for encoding.  
  
- Otherwise, if the **Target charset** property in Pipeline Designer is specified, its value is used.  
  
- Otherwise, if the **codepage** property in the flat file schema is specified, its value is used.  
  
- Otherwise, if the **XMLNorm.SourceCharset** property is specified, its value is used.  
  
- Otherwise, "UTF-8" is used. Note that the Flat File Assembler pipeline component does not put byte order mark on outgoing messages when UTF-8 encoding is used.  
  
  The Flat File Assembler saves encoding information on the body part of the BizTalk message object in the **IBaseMessagePart.Charset** property.  
  
## See Also  
 [Flat File Assembler Pipeline Component](../core/flat-file-assembler-pipeline-component.md)   
 [How to Configure the Flat File Assembler Pipeline Component](../core/how-to-configure-the-flat-file-assembler-pipeline-component.md)   
 [Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)