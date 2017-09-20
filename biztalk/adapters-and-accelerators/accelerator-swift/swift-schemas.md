---
title: "SWIFT Schemas | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SWIFT, SWIFT messages"
  - "schemas, SWIFT"
  - "SWIFT messages, SWIFT schemas"
  - "SWIFT, schemas"
ms.assetid: 53017a56-a718-4577-a08c-9c92d9a54e7a
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SWIFT Schemas
[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] sends and receives SWIFT financial (FIN) messages as individual flat files over the SWIFT network. Each individual message consists of a set of header blocks, a text block made up of a predefined set of labeled fields and positional or ordered subfields, and a set of trailers inside a trailer block. The content of the text block varies by message type.  
  
 There are also many applications, which exchange batches of SWIFT financial (FIN) messages—a set of messages contained in a single file. The file may be delivered locally or may be transmitted through FileAct (over the SWIFT IP Network—SIPN), or through FTP.  
  
 To simplify the manipulation of the data associated with these messages, regardless of whether they are batched or submitted individually, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] provides an XSD schema defining each message type. This schema promotes the message type so that messages can be automatically associated with the proper schema, and automatically transformed between the external flat file representation, used by the SWIFT network, to and from XML.  
  
 The schema includes all of the blocks including headers, text, and trailers. This schema is an interchange schema, because it is comprehensive enough to transmit messages over the SWIFT network using the FIN message-level protocols, and to contain all of the information associated with a message received through the SWIFT network.  
  
 The schema for each message type defines the overall format and context of that message type. A4SWIFT defines each block. Inside each block, the fields and subfields are laid out. As appropriate, the fields and subfields are built from common base or complex types, defined in separate schemas. Schema-level validation includes format, character set, value set, range, required/optional, repeatability, position, and length, as appropriate. The business rules perform cross-field validations and other logical checks.  
  
 This section contains:  
  
-   [Sample Message Presentation](../../adapters-and-accelerators/accelerator-swift/sample-message-presentation.md)  
  
-   [Sample Schema Presentation](../../adapters-and-accelerators/accelerator-swift/sample-schema-presentation.md)  
  
-   [SWIFT Headers](../../adapters-and-accelerators/accelerator-swift/swift-headers.md)  
  
-   [SWIFT Text](../../adapters-and-accelerators/accelerator-swift/swift-text.md)  
  
-   [SWIFT Trailers](../../adapters-and-accelerators/accelerator-swift/swift-trailers.md)  
  
-   [Updating SWIFT Message Standards](../../adapters-and-accelerators/accelerator-swift/updating-swift-messaging-standards.md)