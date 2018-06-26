---
title: "Character Encoding in the XML Assembler Pipeline Component | Microsoft Docs"
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
  - "pipeline components, XML Assembler"
  - "XMLNorm.TargetCharset property"
  - "Target Charset property"
  - "XML Assembler [pipeline component], character encoding"
ms.assetid: c031fbbf-f00f-41ba-8ac9-cec7d625cef6
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Character Encoding in the XML Assembler Pipeline Component
The XML Assembler pipeline component can produce messages in user-specified character encoding in two ways, as shown in the following table.  
  
|Encoding level|Encoding method|  
|--------------------|---------------------|  
|Component|Set the **Target charset** component property in Pipeline Designer.|  
|Message|Set the **XMLNorm.TargetCharset** property on the message context. **Note:**  A message context property always overrides any context property set in Pipeline Designer.|  
  
 The XML Assembler uses the following algorithm to determine output message encoding:  
  
1. If the **XMLNorm.TargetCharset** context property is set, its value is used.  
  
2. Otherwise, if the **Target charset** property is specified in Pipeline Designer, its value is used.  
  
3. Otherwise, if the **XMLNorm.SourceCharset** property is specified, its value is used.  
  
4. If none of the preceding properties is set, UTF-8 encoding is used.  
  
   The XML Assembler saves the encoding information of a BizTalk message object in the `IBaseMessagePart.Charset` property. When using Unicode or UTF-8 encoding, the XML Assembler always adds the byte order mark (BOM) to outgoing messages.  
  
   Note that when using the default XML send pipeline, which contains the XML Assembler component, the produced documents may be encoded by using the same charset as when they were submitted into the server, or they may be encoded by using UTF-8 if documents were created within the server and **XMLNorm.TargetCharset** was not specified.  
  
## See Also  
 [XML Assembler Pipeline Component](../core/xml-assembler-pipeline-component.md)   
 [How to Configure the XML Assembler Pipeline Component](../core/how-to-configure-the-xml-assembler-pipeline-component.md)   
 [Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)