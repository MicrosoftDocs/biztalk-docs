---
title: "SWIFT Disassembler and Assembler Functionality | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "disassembler, about disassembler"
  - "assembler, about assembler"
  - "assembler, functionality"
  - "disassembler, functionality"
ms.assetid: d4fc092e-586d-4360-921d-151af66b8bc1
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SWIFT Disassembler and Assembler Functionality
The SWIFT disassembler can perform the following tasks when invoked in a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] receive pipeline:  
  
- Dynamically discover the message type and resolve document schema. This enables a single receive port and pipeline to handle multiple SWIFT message types.  
  
- Parse a SWIFT flat file into XML.  
  
- Invoke the XML validating reader to perform XML (schema) validation, such as checking data type validity, data format, or length conformance.  
  
- Invoke the Business Rule Engine (BRE) to perform BRE validation, such as checking conformance to SWIFT network rules or performing other complex validation that the schema does not implement.  
  
- Publish a parsed XML message to the MessageBox database with promoted context properties and serialized error collection XML (providing information about any errors encountered during parsing or validation).  
  
  > [!NOTE]
  >  If the disassembler encounters fatal failures during parsing, the disassembler will publish the message to the MessageBox database in native flat file format rather than XML.  
  
- Process inbound batches, as follows:  
  
  -   Parse and preserve batch envelopes (batch header, batch trailer)  
  
  -   Parse and preserve message envelopes (message header, message trailer)  
  
  -   Parse and validate SWIFT messages in the batch individually  
  
  -   Publish SWIFT messages to the MessageBox database individually  
  
  -   Publish the entire inbound batch to the MessageBox database as a single message (exact copy of input)  
  
  -   Promote batch-related context properties for sorting or correlating messages originating from the same batch  
  
  The SWIFT assembler can perform the following tasks when invoked in a BizTalk send pipeline:  
  
- Dynamically discover the message type and resolve the document schema. This allows a single send port and pipeline to handle multiple SWIFT message types.  
  
- Serialize parsed XML into a SWIFT flat file.  
  
## See Also  
 [Working with the SWIFT Disassembler and Assembler](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)