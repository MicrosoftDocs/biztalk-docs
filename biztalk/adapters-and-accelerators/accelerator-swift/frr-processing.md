---
title: "FRR Processing | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FRR, processing"
  - "FRR, components"
  - "FRR, process flow"
ms.assetid: 8b064d18-5ee7-44fd-95d1-9a0d66f1ad1a
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# FRR Processing
The [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] FIN Response Reconciliation (FRR) feature correlates FIN messages from the SWIFT Alliance Access (SAA) with the original message from [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] that the SAA message responds to. Whenever [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] sends an original message, FRR caches a copy of any message that is bound for SWIFT and that has not failed processing. It then monitors the MessageBox for response messages returned by SAA to [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)], and picks up any ACK/NAK messages that corresponds to the cached message copy.  

 FRR establishes a correlation between an outgoing message and an incoming message by comparing correlation ID properties. FRR sets promoted properties of the copy of the original message according to the nature of the response, and then routes the original message to the MessageBox for further processing.  

## FRR Components  
 FRR includes an ongoing process (orchestration) that monitors outgoing and incoming messages, and for each outgoing or incoming message, promotes the identification properties that it will use for comparison. A series of [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] components work together with the FRR orchestration, routing messages between the FRR components within [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)], and between [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] and SAA. These components are listed below:  

- An FRR receive location that receives the original message from the back-end application.  

- The FRR orchestration that monitors outgoing and incoming messages, and establishes the correlation between them.  

- An FRR send port that sends the original message from [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] to SAA.  

- The BizTalk Adapter for MQSeries that enables data transmission between [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and SAA (which uses MQSeries queues).  

- An FRR receive location that receives FIN response messages from SAA.  

- A set of FRR send ports, each of which sends correlated messages of a specific type from [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] to a back-end application for custom processing.  

  To the above components, you can add a back-end custom handler that processes the original message the promoted properties of which have been set by FRR.  

## FRR Process Flow  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] performs the reconciliation in the following process:  

1. The back-end application routes the original message to [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].  

2. An FRR receive location receives the message, processes it in the associated receive pipeline, and routes it to the BizTalk MessageBox.  

   > [!NOTE]
   >  You can use FRR in conjunction with the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Message Repair and New Submission feature, or separately. If you have installed Message Repair and New Submission, you can configure the system for message repair after step 2. The message-repair orchestration routes the repaired/verified/approved message back to the BizTalk MessageBox for subsequent FRR processing.  

3. If the message in the MessageBox is bound for SWIFT and has passed validation, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] activates an instance of the FRR orchestration. The orchestration keeps a copy of the outgoing message. It then waits in an activated state for a response from SAA, so it can match the outgoing message to any incoming response. This instance of the orchestration only processes that specific outgoing message and any correlated responses to that message. Any other message, even of the same type, is processed by another instance of the orchestration.  

4. At the same time that [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] activates the FRR orchestration instance, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] routes the message to the send port that sends messages to SAA. The send pipeline promotes a message-identification property and properties required for processing by MQSeries. It then sends the message to the BizTalk Adapter for MQSeries.  

5. The BizTalk Adapter for MQSeries transports the message to the appropriate MQSeries queue at SAA.  

6. SAA generates an immediate response for routing directly back to [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]. SAA then routes the message to the SWIFT Network. The SWIFT Network generates other responses, which it sends to SAA for routing back to [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]. SAA sets the correlation token property for the FIN response message to the message-identification value of the original message.  

7. SAA transports the FIN response through the BizTalk Adapter for MQSeries back to [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].  

8. The FRR receive location receives the response and routes the message through the FRR receive pipeline that processes the response's correlation token. It then places the response in the BizTalk MessageBox.  

9. The FRR orchestration instance picks up any message from the MessageBox that has a correlation token equal to the message ID property of the copy of the original message.  

10. If the response indicates that the original message was successfully processed by SAA/SWIFT, the FRR orchestration instance sets the A4SWIFT_Failed promoted property of the copy of the original message to False, and sets the BTS.Operation property to the appropriate value.  

11. If the original message was not successfully processed by SAA/SWIFT, the FRR orchestration instance sets the BTS.Operation property to the appropriate value, and then designates the message for repair by setting A4SWIFT_Failed to True and setting the A4SWIFT_FRRFailedReason promoted property to the reason for the failure.  

12. The FRR orchestration instance discards the response message(s), and then routes the copy of the original message (with promoted properties indicating the response) to the MessageBox.  

13. One of the FRR send ports set up to route the responses to one or more custom handlers picks up the copy of the original message with the promoted properties.  

14. The custom handler or handlers subscribes to, retrieves, and processes the copy of the original message as required for the back-end application.
