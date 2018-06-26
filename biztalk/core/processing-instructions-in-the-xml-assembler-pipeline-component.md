---
title: "Processing Instructions in the XML Assembler Pipeline Component | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "XMLNorm.ProcessingInstructionOption property"
  - "envelopes, processing instructions"
  - "XML Assembler [pipeline component], processing instructions"
  - "Processing instruction scope property"
  - "XMLNorm.ProcessingInstruction property"
  - "envelopes, XML Assembler [pipeline component]"
  - "pipeline components, XML Assembler"
ms.assetid: d8ea453e-3b20-417d-bf25-9d424b0150fd
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Processing Instructions in the XML Assembler Pipeline Component
Processing instructions provide information to the application that processes an XML document. Such information may include instructions about how to process the document, how to display it, and so on.  
  
 Processing instructions are added to an XML document by the **Add processing instructions** property (or the equivalent **XMLNorm.ProcessingInstructionOption** property on the message context). Processing instruction text is specified with the **Add processing instructions text** property (or the equivalent **XMLNorm.ProcessingInstruction** property on the message context).  
  
 The **Add processing instructions** property (or **XMLNorm.ProcessingInstructionOption** property) has three possible values, which are described in the following table.  
  
|Value|Value|Description|  
|-----------|-----------|-----------------|  
|Append|0|New processing instructions from the XML Assembler are appended to the processing instructions at the beginning of the document.|  
|Create new|1|New processing instructions from the XML Assembler overwrite existing processing instructions at the beginning of the document.|  
|Ignore|2|Processing instructions at the beginning of the document are removed.|  
  
 The pair of processing instructions (or message context properties) specified on a message context take precedence over the property pair specified in Pipeline Designer. For example, if **XMLNorm.ProcessingInstructionOption** is specified as **Create new** (1) and **XMLNorm.ProcessingInstruction** is not specified, an empty processing instruction will replace an existing processing instruction.  
  
 As another example, if **XMLNorm.ProcessingInstruction** is specified but **XMLNorm.ProcessingInstructionOption** is not, none of the properties from the message context are used. In this case, the processing instructions from Pipeline Designer are used.  
  
 By default, **Add processing instructions** is set to **Append**, and **Add processing instructions text** is empty.  
  
## Processing Properties and Envelopes  
 Because processing instructions are not preserved for the envelopes, the following combination of flat file assembler settings results in only the outermost envelope having the processing instruction:  
  
- **Processing instruction scope** property set to "Envelope."  
  
- **Add processing instructions** property set to "Append."  
  
  The envelope would use the processing instruction specified in the assembler's **Add Processing instructions text** property.  
  
  Any existing processing instructions in either the outer or inner envelope(s), as specified in the incoming message, will not be present in the output message(s).  
  
## See Also  
 [XML Assembler Pipeline Component](../core/xml-assembler-pipeline-component.md)   
 [How to Configure the XML Assembler Pipeline Component](../core/how-to-configure-the-xml-assembler-pipeline-component.md)   
 [Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)