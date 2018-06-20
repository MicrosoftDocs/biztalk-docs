---
title: "Acknowledgments Processing | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "acknowledgements, processing"
ms.assetid: 705bc12d-69ac-4641-a45e-4f1fab507e4a
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Acknowledgments Processing
The HL7 specification supports exchange of messages in two formats:  
  
- Unsolicited update and its acknowledgment (ACK)  
  
- Query and its response  
  
  In response to a message from an initiating application, the responding application responds with a message that includes data or an error indication. The initiating application may receive a reject status from the responder application indicating that the responder application did not receive the message correctly. In both cases, the process of message exchange involves two entities, the initiating and responding applications. Each is both a sender and receiver of messages. The initiating application sends first and then receives, while the responding system receives and then sends.  
  
## Unsolicited updates  
 An unsolicited update occurs when a line-of-business (LOB) application publishes a message, or initiates a transfer of information when a trigger event occurs. For example, when the laboratory results for a patient are available, there may be a need to send the laboratory results to several other systems. These updates are unsolicited updates to which an ACK responds.  
  
## Queries  
 In the case of a query, an application that requires information sends a query to another application, and the receiving application responds to the query. For example, a pharmacy application may send a request message containing the ID number of the patient to the Order Entry (CPOE) system and receive a response containing the necessary data to permit processing of the order. This requesting transaction is a query, and is different from an unsolicited update. The information that flows between the two applications is contained in the response. The response itself does not require an acknowledgment with a fourth message. However, you can modify this in some environments to respond with an ACK. [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) responds with an ACK if so configured. For an example of a query/response exchange, see [Interrogative Tutorial](../../adapters-and-accelerators/accelerator-hl7/interrogative-tutorial.md).  
  
## In This Section  
  
-   [Validating Messages](../../adapters-and-accelerators/accelerator-hl7/validating-messages.md)  
  
-   [ACK Message Modes](../../adapters-and-accelerators/accelerator-hl7/ack-message-modes.md)  
  
-   [ACK Process Model](../../adapters-and-accelerators/accelerator-hl7/ack-process-model.md)