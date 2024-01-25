---
description: "Learn more about: Document Structure Enforcement in the XML Assembler Pipeline Component"
title: "Document Structure Enforcement in the XML Assembler Pipeline Component"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Document Structure Enforcement in the XML Assembler Pipeline Component
If document or envelope schemas are explicitly referenced in the XML Assembler, the XML Assembler ensures that only documents with the message type corresponding to referenced schemas are processed. All the other documents are not processed even though a schema may be deployed for them.  
  
> [!NOTE]
>  The envelope schema is taken from the first message only. The properties for the envelope are always taken from the first message.  
  
## See Also  
 [XML Assembler Pipeline Component](../core/xml-assembler-pipeline-component.md)   
 [How to Configure the XML Assembler Pipeline Component](../core/how-to-configure-the-xml-assembler-pipeline-component.md)   
 [Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)
