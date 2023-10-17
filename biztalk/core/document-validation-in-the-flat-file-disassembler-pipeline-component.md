---
description: "Learn more about: Document Validation in the Flat File Disassembler Pipeline Component"
title: "Document Validation in the Flat File Disassembler Pipeline Component | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Validate Document Structure property"
  - "FFDasm.ValidateDocumentStructure property"
  - "Flat File Disassembler [pipeline component], validating documents"
  - "pipeline components, Flat File Disassembler"
ms.assetid: 8cd777e4-8aba-4c17-92e8-958e5dd57d09
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Document Validation in the Flat File Disassembler Pipeline Component
By default, the Flat File Disassembler component does not validate documents it processes. However, you can turn validation on by setting the **Validate document structure** property on the component to **True**, or by setting the **FFDasm.ValidateDocumentStructure** message context property to **True**. When document validation is set to run, the Flat File Disassembler validates the document structure as well as the header and trailer structures to ensure that they conform to the document, header, and trailer schemas.  
  
 The Flat File Disassembler can remove empty fields and records when **suppress_empty_nodes="True"** is specified by the **schemaInfo** annotation in the flat file XSD schema. If you use the **schemaInfo** annotation in this way, the Flat File Disassembler removes empty fields and records regardless of whether they are optional. This may cause validation errors if you use XML validation (either by setting the Flat File Disassembler **Validate document structure** property to **True** or by using the XML Validator pipeline component). If a validation error occurs, the message is suspended. For more information about the suppress_empty_nodes property, see [Additional Flat File Properties](../core/additional-flat-file-properties.md).  
  
## See Also  
 [Flat File Disassembler Pipeline Component](../core/flat-file-disassembler-pipeline-component.md)   
 [How to Configure the Flat File Disassembler Pipeline Component](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md)   
 [Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)
