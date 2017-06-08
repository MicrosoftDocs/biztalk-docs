---
title: "How to Configure the Flat File Disassembler Pipeline Component | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Flat File Disassembler [pipeline component], configuring"
  - "pipeline components, Flat File Disassembler"
  - "messages, flat files"
ms.assetid: c09996f6-6035-42a3-a75f-4def4ac39a95
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure the Flat File Disassembler Pipeline Component
The Flat File Disassembler pipeline component is used for disassembling documents in flat file format and converting them into XML format.  
  
### To configure the properties for the Flat File Disassembler pipeline component  
  
1.  Drag the Flat File Disassembler pipeline component into the Disassemble stage of a receive pipeline.  
  
2.  In the Properties window, in the **Pipeline Component Properties** section, do the following.  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Document schema**|Select a flat file document schema to use for parsing the message from flat file to XML format. The flat file document schema for parsing can be created in BizTalk Editor.<br /><br /> Default value: None **Note:**  You must specify a schema for this property, or a compile-time error will occur.|  
    |**Header schema**|Select a schema for the header part of the flat file message. The schema for the header part of the flat file message can be created in BizTalk Editor.<br /><br /> Default value: None|  
    |**Preserve header**|Set this property to **True** if you need to store the flat file message header on the message context. Preserving the header of the flat file message enables the header structure and content to flow with the message through BizTalk Server. The header can then be used when serializing the message back to flat file format in the Flat File Assembler pipeline component.<br /><br /> When the preserved header is being serialized by the Flat File Assembler, the header document design-time property can lack the name of the header schema, because this information can be obtained dynamically at run time. This is accomplished by using the message type of the preserved header.<br /><br /> Default value: **False**|  
    |**Trailer schema**|Select a schema for the trailer part of the flat file message. The schema for the trailer part of the flat file message can be created in BizTalk Editor.<br /><br /> Default value: None|  
    |**Recoverable interchange processing**|When "false" - indicates that entire interchange is disassembled as a unit (if any contained message fails, entire interchange is suspended).<br /><br /> When "true" - indicates that messages within interchange are extracted individually by disassembler with possibility of some propagating through messaging pathway and others being suspended.<br /><br /> For more information on recoverable interchange processing, see [Recoverable Interchange Processing](../core/recoverable-interchange-processing.md).|  
    |**Validate document structure**|Set this property to **True** if you need to validate all the parts of the flat file message (header, body, and trailer) to make sure they conform to their schemas. This option reduces the performance of the Flat File Disassembler, so it is set to **False** by default.<br /><br /> Default value: **False**|  
  
## See Also  
 [Flat File Disassembler Pipeline Component](../core/flat-file-disassembler-pipeline-component.md)   
 [Configuring Native Pipeline Components](../core/configuring-native-pipeline-components.md)   
 [XML and Flat File Property Schema and Properties](../core/xml-and-flat-file-property-schema-and-properties.md)   
 [Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)