---
description: "Learn more about: How to Configure the Flat File Assembler Pipeline Component"
title: "How to Configure the Flat File Assembler Pipeline Component | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pipeline components, Flat File Assembler"
  - "Flat File Assembler [pipeline component], configuring"
  - "messages, flat files"
ms.assetid: 5af61bba-4eb2-4bb9-a655-394a76d08d3b
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure the Flat File Assembler Pipeline Component
The Flat File Assembler pipeline component is used to serialize an XML document into delimited or positional flat file format before sending it out of the server.  
  
### To configure the properties for the Flat File Assembler pipeline component  
  
1.  Drag the Flat File Assembler pipeline component into the Assemble stage of the send pipeline.  
  
2.  In the Properties window, in the **Pipeline Component Properties** section, do the following.  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Document schema**|Select a flat file document schema to use for serializing the message from XML to the flat file format. If no schema is specified, run-time schema discovery is done. You can create the flat file document schema in BizTalk Editor.<br /><br /> Default value: None|  
    |**Header schema**|Select a schema for the header part of the flat file message. A header schema can also be specified in the message context property named **HeaderSpecName** under the xmlnorm namespace. In this case, it will override the header schema specified in Pipeline Designer.<br /><br /> You can create the schema for the header part of the flat file message with BizTalk Editor.<br /><br /> Default value: None|  
    |**Preserve byte order mark**|Specifies whether to add a byte order mark (BOM) to the document produced by the assembler component.<br /><br /> Default Value: **False**|  
    |**Target charset**|Specifies the target character set used for encoding of outgoing messages.<br /><br /> Default value: None|  
    |**Trailer schema**|Select a schema for the trailer part of the flat file message. You can create the schema for the trailer part of the flat file message in BizTalk Editor.<br /><br /> Default value: None|  
  
## See Also  
 [Flat File Assembler Pipeline Component](../core/flat-file-assembler-pipeline-component.md)   
 [Configuring Native Pipeline Components](../core/configuring-native-pipeline-components.md)   
 [XML and Flat File Property Schema and Properties](../core/xml-and-flat-file-property-schema-and-properties.md)   
 [Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)
