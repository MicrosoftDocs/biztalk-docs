---
title: "Document Structure Enforcement in the XML Assembler Pipeline Component | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Add XML declaration property"
  - "pipeline components, XML Assembler"
ms.assetid: c121ec4b-c02b-4626-a5be-2937500dbefa
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Document Structure Enforcement in the XML Assembler Pipeline Component
If document or envelope schemas are explicitly referenced in the XML Assembler, the XML Assembler ensures that only documents with the message type corresponding to referenced schemas are processed. All the other documents are not processed even though a schema may be deployed for them.  
  
> [!NOTE]
>  The envelope schema is taken from the first message only. The properties for the envelope are always taken from the first message.  
  
## See Also  
 [XML Assembler Pipeline Component](../core/xml-assembler-pipeline-component.md)   
 [How to Configure the XML Assembler Pipeline Component](../core/how-to-configure-the-xml-assembler-pipeline-component.md)   
 [Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)