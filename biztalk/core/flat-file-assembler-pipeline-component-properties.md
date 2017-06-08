---
title: "Flat File Assembler Pipeline Component Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Microsoft.BizTalk.Component.FFAsmComp"
ms.assetid: ea54099a-c907-4f51-b020-747534a4b907
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Flat File Assembler Pipeline Component Properties
Use the Flat file assembler pipeline component to serialize XML documents into a flat file format and optionally add a header and/or trailer to it.  
  
 The Flat file assembler pipeline component is intended for use in the Assemble stage of the Send pipeline.  
  
 The properties of the Flat file assembler pipeline component can be set in the Properties window of Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. To display the Properties window, select the component, right-click and select **Properties**, or press F4. The following table contains the configurable Flat file assembler pipeline component properties.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Document schema**|Select a flat file document schema to use for serializing the message from XML to the flat file format. If no schema is specified, runtime schema discovery will be used.<br /><br /> Default value: (None)|  
|**Header schema**|Select a schema for the header part of the flat file message. If no schema is specified, but header information is available at runtime, the corresponding header will be used.<br /><br /> Default value: (None)|  
|**Preserve byte order mark**|Specifies whether to add a byte order mark (BOM) to the documents produced by the assembler component.<br /><br /> Default value: False|  
|**Target charset**|Identify the character set used for the encoding of outgoing messages.<br /><br /> Default value: (None)|  
|**Trailer schema**|Select a schema for the trailer part of a flat file message.<br /><br /> Default value: (None)|  
  
## See Also  
 [Using Pipeline Designer](../core/using-pipeline-designer.md)   
 [How to Configure the Flat File Assembler Pipeline Component](../core/how-to-configure-the-flat-file-assembler-pipeline-component.md)   
 [Character Encoding in the Flat File Assembler Pipeline Component](../core/character-encoding-in-the-flat-file-assembler-pipeline-component.md)   
 [Property Demotion in Assembler Pipeline Components](../core/property-demotion-in-assembler-pipeline-components.md)   
 [Document Structure Enforcement in the Flat File Assembler Pipeline Component](../core/document-structure-enforcement-in-the-flat-file-assembler-pipeline-component.md)   
 [How to Configure the Flat File Disassembler Pipeline Component](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md)