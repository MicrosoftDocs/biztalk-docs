---
title: "BTAHL72XML Processing | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "2.XML messages, processing"
  - "acknowledgements, 2.XML messages"
  - "2.XML messages, message modes"
  - "message modes, 2.XML message"
  - "2.XML messages"
  - "validating, 2.XML messages"
  - "2.XML messages, acknowledgements"
  - "2.XML messages, validating"
ms.assetid: 2f12cb44-816c-4773-9db0-9cbc3d1b1aee
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BTAHL72XML Processing
The following components in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) process HL7 2.XML (XML-encoded) messages:  
  
- Pipelines and core libraries: [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].PipelineCommon.dll and [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].PipelineMessageCore.dll  
  
- Assembler and disassembler libraries: [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].HL72XmlAsm.dll and [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].HL72XmlDAsm.dll  
  
- The acknowledgment (ACK) validation library used for the two-way MLLP send adapter: [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].HL7ACKHelper.dll  
  
## XML Message Modes  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] supports the following message modes for 2.XML messages:  
  
- Publisher-subscriber (pub-sub) mode  
  
   The publisher broadcasts to a party of subscribers, either as declarative or an unsolicited update. [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] provide flexibility to this mode, since you can manage subscriptions and parties after design time.  
  
- Request-response mode  
  
   An interrogative or query message exchange in which a specific request from a specific entity results in a responding message.  
  
## XML Validation  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] provides the following validation of 2.XML messages:  
  
- XML reader  
  
- Schematic  
  
   You enable or disable schematic validation by the party. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] uses the HL7 2.XML schemas directly for this processing, as determined by the MSH9.3 message-structure header field and the MSH12 Version ID field (2.3.1, 2.4, or 2.5). [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] uses the standard XML processing capabilities in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  
  
- Z segment  
  
   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] validates that no declared segments are included in an undeclared Z segment.  
  
## ACK Generation  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] supports the following types of acknowledgments (ACKs) for 2.XML messages. Both the HL7 error type and the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] (alternate) error type are used:  
  
-   HL7 original ACKs  
  
-   HL7 enhanced ACKs  
  
     Commit Accept and Application Accept  
  
## See Also  
 [Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [Using HL7 2.XML Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md)