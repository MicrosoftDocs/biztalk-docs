---
title: "How BTAHL7 Routes Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "routing, about routing"
  - "routing, messages"
  - "messages, routing"
  - "BTAHL7, message routing"
ms.assetid: 555696c7-6023-44eb-b13d-cf7527bbc92f
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How BTAHL7 Routes Messages
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) leverages the message processing capabilities of [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], but also extends it in several ways that are specific to HL7 messaging requirements.  

## Routing overview

HL7 receives messages from a Line of Business (LOB) system, and may receive them using the MLLP adapter. The LOB system connects to MLLP adapter on [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] over a TCP port, and then sends messages to the MLLP adapter.

In **[!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)] and older versions**, the HL7 MLLP receive transport adapter waits for the remote LOB system to connect to MLLP. Once the remote LOB system connects, the LOB system sends the messages using MLLP to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Specifically: 

1. The remote LOB system connects to the MLLP adapter on the local [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] using a TCP port 
2. The BTA4HL7 receive location with MLLP Adapter accepts the connection 
3. The remote LOB system delivers one or more messages 
4. The remote LOB system disconnects

In **[!INCLUDE[bts2016_md](../../includes/bts2016-md.md)] and newer versions**, the connection to the LOB system is initiated by the MLLP adapter, and then the LOB system pushes messages to the MLLP receive. In other words, the remote LOB system waits for the connection before sending messagings to MLLP. Specifically: 

1. The local [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] connects to the remote LOB system using a TCP port 
2. The BTA4HL7 receive location with MLLP adapter initiates the connection 
3. The remote LOB system delivers one or more messages 
4. The remote LOB system disconnects 

For backwards-compatibility, you can use the original default behavior where the remote LOB system initiates the connections. This option is configurable in the MLLP receive location properties. 
 
Once the HL7 message is received, it is then submitted to an HL7 receive pipeline. Within this pipeline, the HL7 disassembler will parse the message, and will validate the message according to the appropriate schema definition and validation configuration. At this point, an HL7 acknowledgment message may be generated (success or error), according to the validity of the message and the relevant acknowledgment configuration. From here, the pipeline will submit the message instance and optional acknowledgment to the MessageBox database for further processing and routing.  
  
 Once a message instance arrives in the MessageBox database, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] checks filter-based subscriptions and routes the message to one or more send ports (possibly MLLP ports) through an HL7 send pipeline. The send pipeline may validate the message instances according to the appropriate schema definition and validation configuration. In addition to validation, it is possible to override certain field values in the MSH segment of the outgoing message. This override ability is especially useful if multiple ports have subscribed to a message and each receiving application has unique expectations within the MSH segment values.  
  
 Of course, all of the other [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] send and receive port capabilities will be available to HL7 messages, along with some capabilities that may be unique to the selected port type, such as MLLP send-port parameters. An example of the relevant [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] capabilities would be the ability to apply a transformation map to an outbound message.  
  
## How Routing Works

The [!INCLUDE[btaBTAHL7NoNumber_md](../../includes/btabtahl7nonumber-md.md)] routes HL7 message instances according to subscriptions that the MessageBox database manages. These subscriptions use filters that you define for each send port. Example filters might include routing based on receive port ID and/or HL7 message type (ADT^A03, for example) and/or sending application (MSH3.1 value).  
  
 In addition to setting up [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] subscriptions, you need to perform some HL7-specific messaging configuration that will affect HL7 message instances as [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] routes them. This additional configuration enables you to apply unique HL7 validation rules, automatic generation of acknowledgments, and the ability to override MSH values. [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] applies this configuration at the party level. You need to define parties within BizTalk Explorer and perform the related HL7 configuration within [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] Configuration Explorer.  
  
 To apply unique HL7 messaging configuration (for example, validation or MSH overrides) to multiple send ports that subscribe to a message, you need to create associations between parties and send ports. You configure party-to-send port associations as party properties within BizTalk Explorer.  
  
 If you do not need to route HL7 messages to multiple send ports, or apply unique HL7 processing configuration to multiple send ports, you can eliminate the step of associating parties with send ports. In this case, [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] associates the party with its HL7 messaging configuration through the receiving application field in the HL7 message (MSH 3.1). This situation is most likely to occur in an HL7 interrogative (request/response) message exchange.  
  
## See Also  
 [Message Validation](../../adapters-and-accelerators/accelerator-hl7/message-validation.md)