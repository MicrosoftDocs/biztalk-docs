---
title: "Message Modes | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "message modes, about message modes"
  - "messages, message modes"
  - "message modes, HL7 messages"
ms.assetid: 2d832b67-6f0e-45e1-95ac-cb80b74a7831
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Modes
There are two basic concepts that underlie all HL7 messages. These concepts address different ways in which independent systems that exchange data can interact, and provide a structure that supports the requirements of interoperability over time within a distributed health care system. The concepts listed below define the underlying themes behind the HL7 design:  
  
- **Messaging Mode**. The recognition of three fundamental purposes for information exchange: to broadcast information (declarative), to request information (interrogative), and to request that the system take an action (imperative). Each of these purposes has its particular requirements and pattern of message flow.  
  
- **Acknowledgment Mode**. The need to support tightly and loosely coupled styles of messaging. The acknowledgment modes for HL7 enable a sending application either to require a response from the receiver, or to enable the underlying network to guarantee message delivery.  
  
- **Localization**. The need to support specific local requirements by allowing entities to introduce site-specific material into message specifications.  
  
- **Evolution**. The need to support sites with many interfaces and many applications by enabling interoperability between standard versions. This enables entities to stage interface upgrades, as opposed to requiring simultaneous upgrades of all interfaces.  
  
  The following functions of [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) support the above requirements:  
  
- HL7 acknowledgment modes. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] supports the original acknowledgment mode by passing application acknowledgments back to the original message sender.  
  
- Different messaging modes. This enables broadcast to multiple destinations, and ties together queries to the associated query response.  
  
- Support for multiple versions, including XML and pipe-delimited encodings.  
  
- Mapping between HL7 versions to enable diverse environments and upgrades.  
  
- Localization (customization) within orchestration.  
  
- Tools to support debugging and evaluation of new interfaces.  
  
## See Also  
 [Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [Using HL7 2.X Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)   
 [Using HL7 2.XML Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md)   
 [Message Types and Events](../../adapters-and-accelerators/accelerator-hl7/message-types-and-events.md)   
 [HL7 Messaging](../../adapters-and-accelerators/accelerator-hl7/hl7-messaging.md)