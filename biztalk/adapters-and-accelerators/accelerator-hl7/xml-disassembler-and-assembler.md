---
title: "XML Disassembler and Assembler | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "disassembler, XML"
  - "assembler, XML"
ms.assetid: 242a7a96-2342-4ab5-9d3f-1acbcc7ffd14
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# XML Disassembler and Assembler
The XML disassembler and assembler ensure that [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) not only supports HL7-encoded messages, but also supports incoming and/or outgoing XML messages.  
  
## XML Disassembler  
 The XML disassembler parses incoming XML messages into XML segments for processing. As it parses the messages, the disassembler performs the following tasks:  
  
- Handles escape sequences  
  
- Handles checks of required/optional properties  
  
- Handles declared Z segments  
  
  As it parses the messages, the dissassembler performs the following:  
  
- Syntactic validation  
  
- Schema validation (if enabled)  
  
## XML Assembler  
 The XML assembler serializes XML segments into an outgoing XML message. The XML assembler supports and creates the following acknowledgment (ACK) messages:  
  
- Static  
  
- Original mode  
  
- Enhanced mode  
  
  The XML assembler also has the ability to route deferred ACK messages.  
  
## See Also  
 [BTAHL72XML Processing](../../adapters-and-accelerators/accelerator-hl7/btahl72xml-processing.md)   
 [BizTalk Accelerator for HL7 Components](../../adapters-and-accelerators/accelerator-hl7/biztalk-accelerator-for-hl7-components.md)