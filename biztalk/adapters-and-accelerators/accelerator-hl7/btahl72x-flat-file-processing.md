---
title: "BTAHL72X Flat File Processing | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ACKs"
  - "2.X messages, disassembler"
  - "property promotion, MSH-header schemas"
  - "disassembler, validating messages"
  - "HL7, errors"
  - "2.X messages, validating headers"
  - "acknowledgements, generating"
  - "assembler, validating messages"
  - "messages, multi-part messages"
  - "property promotion, property schemas"
  - "generating aknowledgements"
  - "messages, 2.X messages"
  - "schemas, MSH-header schemas"
  - "2.X messages, validating message bodies"
  - "2.X messages"
  - "schemas, property schemas"
  - "message modes, 2.X messages"
  - "errors, HL7 error format"
  - "flat files"
  - "validating, messages"
  - "schemas, property promotion"
  - "headers, validating"
  - "2.X messages, message modes"
  - "2.X messages, header validation"
  - "2.X messages, parsing flat files"
ms.assetid: c92e2f70-0bfa-4bc8-8044-4a6e62cabee3
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BTAHL72X Flat File Processing
The following components in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) process HL7 2.X (HL7-encoded) messages:  
  
- Pipelines and core libraries: [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].PipelineCommon.dll and [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].PipelineMessageCore.dll  
  
- Assembler and disassembler libraries: [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].HL72fAsm.dll and [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].HL72fDAsm.dll  
  
- The acknowledgment (ACK) validation library used for the two-way MLLP send adapter: [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].HL7ACKHelper.dll  
  
## HL7 Message Modes  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] supports the following message modes for 2.X messages:  
  
- Publisher-subscriber (pub-sub) mode  
  
   The publisher broadcasts to a party of subscribers, either as declarative or an unsolicited update. [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] provide flexibility to this mode, since you can manage subscriptions and parties after design time.  
  
- Request-response mode  
  
   An interrogative or query message exchange in which a specific request from a specific entity results in a responding message.  
  
## Flat File Parsing  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] parses HL7 2.X multi-part messages into three parts:  
  
-   Header-MSH part  
  
-   Body part  
  
-   Z part  
  
## HL7 Header Validation  
 The HL7 disassembler and assembler perform structural and schematic validation of the header of a 2.X message, in order to verify that it can process the message. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] bases the schematic validation on the common header schema, MSH_25_GLO_DEF.  
  
 For instance, the parser determines that the MSH1 and MSH2 fields are well formed. MSH1 must have only one character. MSH2 must be between two and four characters, and no characters can repeat.  
  
## HL7 Body Validation  
 The HL7 disassembler and assembler perform basic structural validation of the body of a 2.X message, and schematic validation, if you enable it.  
  
 The basic structural validation of the body, which [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] always performs, includes verifying the following:  
  
- That there are three characters in segments  
  
- That the segment delimiter is \<CR\> or \<CR\>\<LF\> (optional for the last segment)  
  
- That field delimiters are appropriate  
  
- That there are no declared segments (with a defined three-character segment tag) in an undeclared Z segment  
  
  More extensive schema validation of the body includes the following:  
  
- Trailing-field delimiters  
  
   In Header-MSH segment and body segments  
  
- Z segment  
  
- XSD-supported and custom data type  
  
   XSD supported and non-XSD types (TS (Time Stamp), DT (date), TM (time), and TN (telephone number)  
  
- Enumerations  
  
   ID (HL7-defined tables) and IS (user-defined tables)  
  
- Optionality  
  
   Required and optional  
  
- Repetition  
  
   Segment and field  
  
- Escape sequences  
  
   Encoding characters, formatting, and character sets  
  
  You enable or disable schematic validation for all messages received from or sent to a specific party (source party for the disassembler, destination party for the assembler). [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] uses the HL7 2.X schemas directly for this processing, as determined by the MSH9.3 message-structure header field, the MSH12 Version ID field (2.3.1, 2.4, or 2.5), and the namespace setting in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer.  
  
## HL7 Disassembler Processing  
 The HL7 disassembler parses incoming HL7 messages into XML segments for processing. As it parses the messages, the disassembler performs the following tasks:  
  
-   Handles escape sequences  
  
-   Handles checks of the required/optional properties  
  
-   Handles defined segments and undefined or unexpected Z segments (for a description of Z segments, see [Customizing Messages through Z Objects](../../adapters-and-accelerators/accelerator-hl7/customizing-messages-through-z-objects.md)).  
  
-   Ignores unexpected segments at the end of an instance (which become undeclared Z segments)  
  
## Error Reporting  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] reports most errors in standard HL7 error format, which include the segment, sequence, field, and error code. However, the error condition may be such that not all of these are available, for instance, if no schema is present. To handle such cases, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] can report errors in an alternate [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] error format. The error segment in a message includes two parts: one for the HL7 error and one for the alternative [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] error.  
  
## ACK Generation  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] supports the following types of acknowledgments (ACKs) for 2.X messages. Both the HL7 error type and the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] (alternate) error type are used:  
  
-   Mapping original message and ACK  
  
-   HL7 original ACKs  
  
-   HL7 enhanced ACKs  
  
     Commit Accept and Application Accept  
  
-   Static/proxy ACK  
  
     ACK or NAK  
  
## Property Promotion  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] supports promoting the following 2.X properties:  
  
-   Property schema  
  
-   MSH-header schema  
  
## In This Section  
  
-   [Schema Determination in the HL7 2.X Disassembler](../../adapters-and-accelerators/accelerator-hl7/schema-determination-in-the-hl7-2-x-disassembler.md)  
  
-   [Schema Determination in the HL7 2.X Assembler](../../adapters-and-accelerators/accelerator-hl7/schema-determination-in-the-hl7-2-x-assembler.md)  
  
## See Also  
 [Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [Using HL7 2.X Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)