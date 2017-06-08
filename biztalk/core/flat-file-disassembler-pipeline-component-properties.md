---
title: "Flat File Disassembler Pipeline Component Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Microsoft.BizTalk.Component.FFDasmComp"
ms.assetid: 579f9da1-fbdc-4733-846d-cdb6495b8d74
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Flat File Disassembler Pipeline Component Properties
Use the Flat file disassembler pipeline component to parse raw data into one or more documents and optionally remove headers and/or trailers.  
  
 The Flat file disassembler pipeline component is intended for use in the Disassemble stage of a Receive pipeline.  
  
 The properties of the Flat file disassembler pipeline component can be set in the Properties window of Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. To display the Properties window, select the component, right-click and select **Properties**, or press F4. The following table contains the configurable Flat file disassembler pipeline component properties.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Document schema**|Select a flat file document schema to use for parsing the message from flat file to XML format.<br /><br /> Default Value: (None)|  
|**Header schema**|Select a schema for the header part of a flat file message.<br /><br /> Default Value: (None)|  
|**Preserve header**|Set this property to True if you need to store the flat file message header on the message context. Preserving the header of the flat file message enables the header structure and content to flow along with the message through the BizTalk Server and then use this when serializing the message back to a flat file format in the flat file assembler.<br /><br /> When the preserved header is being serialized by the flat file assembler, the header document design-time property can lack the name of the header schema because this information can be obtained dynamically at run time.<br /><br /> Default Value: False|  
|**Trailer schema**|Select a schema for the trailer part of the flat file message.<br /><br /> Default Value: (None)|  
|**Validate document structure**|Set this property to True if you need to validate all the parts of the flat file message (header, body, and trailer) to make sure they conform to their schemas. This option reduces the performance of the flat file disassembler so it is set to false by default.<br /><br /> Default Value: False **Note:**  You must specify a document schema (using the Document schema property) and have it deployed if you want to validate the document structure. If you fail to specify a document schema, you will receive a runtime error.|  
|**Recoverable interchange processing**|Indicate whether to process messages within an interchange individually. For more information, see [Recoverable Interchange Processing](../core/recoverable-interchange-processing.md)<br /><br /> Default Value: False|  
  
## See Also  
 [Using Pipeline Designer](../core/using-pipeline-designer.md)   
 [How to Configure the Flat File Disassembler Pipeline Component](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md)   
 [Flat File Disassembler Pipeline Component](../core/flat-file-disassembler-pipeline-component.md)   
 [Document Validation in the Flat File Disassembler Pipeline Component](../core/document-validation-in-the-flat-file-disassembler-pipeline-component.md)   
 [Character Encoding in the Flat File Disassembler Pipeline Component](../core/character-encoding-in-the-flat-file-disassembler-pipeline-component.md)   
 [Extending the Flat File Disassembler Pipeline Component](../core/extending-the-flat-file-disassembler-pipeline-component.md)   
 [Distinguished Fields in Disassembler Pipeline Components](../core/distinguished-fields-in-disassembler-pipeline-components.md)