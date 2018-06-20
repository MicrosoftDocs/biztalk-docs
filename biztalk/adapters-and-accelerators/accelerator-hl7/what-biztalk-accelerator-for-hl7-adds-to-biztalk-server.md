---
title: "What BizTalk Accelerator for HL7 Adds to BizTalk Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "batching, documents"
  - "BTAHL7, batching"
  - "messages, acknowledgements"
  - "messages, auditing"
  - "Configuration Explorer"
  - "BTAHL7, message validation"
  - "BTAHL7, Configuration Explorer"
  - "messages, processing"
  - "BTAHL7, BizTalk Server"
  - "BTAHL7, message processing"
  - "auditing, messages"
  - "BTAHL7, auditing"
  - "validating, messages"
  - "acknowledgements, messages"
  - "BTAHL7, logging"
  - "BizTalk Server, BTAHL7"
  - "messages, validating"
  - "logging"
  - "BTAHL7, acknowledgements"
  - "errors, logging"
ms.assetid: 862e9f26-588a-4e91-8ebc-f53aab6f46c2
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# What BizTalk Accelerator for HL7 Adds to BizTalk Server
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) builds a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] integration system into a health care integration system. It adds functionality that health care organizations require.  
  
 You install [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] on top of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] adds functionality to the core [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] engine. It adds features, tools, and utilities to those that [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] provides. It also adds application-programming interfaces (APIs) to what the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] SDK provides.  
  
## BTAHL72X Message Processing  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] adds a number of features and tools that enable the system to process HL7 messages natively, without the need for customization. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] includes all the document specifications, applications, and components that you need to develop and deploy for processing the full range of HL7-specific transactions. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] supports [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2X flat-file schemas. The following [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] components perform [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2X message processing:  
  
- HL7 disassembler and assembler that enable the system to parse and serialize HL7 messages natively. The disassembler and assembler are part of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pipeline, which performs a series of processing steps on messages, including conversion to or from XML, decoding or encoding, and message validation.  
  
- A Minimal Lower Layer Protocol (MLLP) adapter that enables the system to receive or send HL7-based messages, which [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] typically transports using the MLLP protocol. The MLLP adapter ensures that [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] are interoperable with HL7-based messaging applications.  
  
- HL7 message schemas that enable the system to receive HL7-encoded messages.  
  
## BTAHL72XML Message Processing  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] adds a number of features and tools that enable the system to process XML messages. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] converts HL7 messages to XML format in order to enable [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], which uses XML internally, to perform operations on messages. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] performs the conversion to XML only for HL7 V2.X messages, since they are natively in flat file format. It does not perform the conversion for 2.XML messages, which are in XML format. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] parses and validates these messages without conversion.  
  
 The XML message schemas supported are the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2XML schemas generated by the HL7 organization for the HL7 V2.XML version, and the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2X schemas used for HL7 V2.X version messages (in flat file format). [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] includes the document specifications, applications, and components that you need to develop and deploy for processing the full range of [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2XML transactions. The following [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] components perform [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2XML message processing:  
  
- XML disassembler and assembler that enable the system to parse and serialize XML messages that correspond to HL7 messages. The XML disassembler and assembler include enhancements beyond the functionality of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] XML disassembler and assembler, including auto-acknowledgment and message validation.  
  
- HL7-compatible XML schemas that enable the system to receive HL7 messages (both V2.X and V2.XML messages). The system converts V2.X messages into XML messages (V2.XML messages are already in XML), and then sends them to another system that is XML-enabled. Similarly, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] can receive XML messages, and then convert them into HL7 for sending. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] transforms HL7-specific data from or to another format by using XML-based document specifications, along with the HL7 parser, maps, and other [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] tools that call the schemas and maps. For example, you might receive an interchange in standard HL7 V2.0 format or V2.5 format, and transform that data into another format that an existing medical application can use.  
  
## Validation  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] performs validation of HL7 V2.X messages that [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] cannot perform. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] automatically performs syntactical and schematic validation of the header of an HL7 message, and automatically performs some structural validation of the body of an HL7 message. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] performs schematic validation of the body of an HL7 message, if you enable that feature (see [Validation Settings](../../adapters-and-accelerators/accelerator-hl7/validation-settings.md)).  
  
 The validation of the body of an HL7-encoded message includes the schema, data format, some header and body fields, and enumeration values. The validation of 2.XML messages includes validation against their schema, which is standard XML validation. For more information, see [BTAHL72X Flat File Processing](../../adapters-and-accelerators/accelerator-hl7/btahl72x-flat-file-processing.md) and [BTAHL72XML Processing](../../adapters-and-accelerators/accelerator-hl7/btahl72xml-processing.md).  
  
## Auto Acknowledgment  
 To ensure reliability of the messaging system, you may want to require acknowledgments (ACK) to HL7 messages that [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] generates automatically based on configuration settings.  
  
 Original-mode ACKs confirm validation of the message header and body. In enhanced mode, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] generates two types of ACKs: an accept ACK that it sends on validation of the header, and an application ACK that it sends on validation of the complete message. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] generates a deferred ACK by the line-of-business application that receives a message from [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  
  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] facilitates acknowledgment processing supporting bidirectional message transports.  
  
## Batching  
 You can process documents in batch mode, which saves processing overhead. You can also batch responses to those batches. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] enables three kinds of batching for HL7 2.X messages:  
  
- Inbound batching, in which the system receives messages as a batch, and then fragments it into individual messages.  
  
- Batch in/batch out, in which the system both receives and sends messages as a batch.  
  
- Create batching, in which the system sends a batch of messages received as individual messages.  
  
  > [!NOTE]
  >  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] does not provide batching capabilities for V2.XML messages.  
  
## Logging  
 To enhance troubleshooting, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] enables reporting of errors or warnings signaled by system components. You can filter such events, store them in any of three log stores ([!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] event log, WMI, or a [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)][!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] log store), or customize them by using the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] SDK.  
  
## Configuration Explorer  
 You can configure [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] parties, batches, acknowledgments, and the log store in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer, an administrative tool added to the tools that [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] provides. This tool also enables you to initiate batch processing at the party level. The [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] SDK enables you to customize these settings programmatically.  
  
## See Also  
 [How BizTalk Server Solves the Business Need](../../adapters-and-accelerators/accelerator-hl7/how-biztalk-server-solves-the-business-need2.md)