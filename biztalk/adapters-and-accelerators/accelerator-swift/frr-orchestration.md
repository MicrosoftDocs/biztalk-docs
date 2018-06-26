---
title: "FRR Orchestration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "messages, promoted properties"
  - "orchestrations, message subscriptions"
  - "promoted properties, messages"
  - "FRR, orchestrations"
  - "subscriptions, messages"
  - "orchestrations, reconciliation time-out"
  - "messages, message/response correlation"
  - "message/response correlation"
  - "promoted properties, FIN Response Reconciliation"
  - "orchestrations, FRR"
  - "outbound messages"
  - "FIN Response Reconciliation, promoted properties"
  - "direct bindings"
  - "reconciliation time-out"
  - "bindings, direct"
  - "messages, subscriptions"
  - "subscriptions, orchestrations"
  - "messages, outbound"
  - "MessageBox database"
ms.assetid: ea8d31c2-ac3b-44ac-8064-d008da4f7f72
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# FRR Orchestration
[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] implements FRR through the FRR orchestration. The orchestration determines whether the Correlation Token of the FIN response matches the message ID of the original message. It processes the message in parallel with the send functions performed by the send port that sends the message to SAA, and with the receive functions performed by the receive location that receives the message from SAA.  
  
 At the highest level, an instance of the orchestration does the following processing:  
  
1. Caches a copy of the original outbound message bound for SAA by listening on the MessageBox.  
  
   > [!NOTE]
   >  [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] creates an instance of the orchestration when [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] routes the original message to the MessageBox.  
  
2. Waits for [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] to publish a FIN response from SAA to the MessageBox.  
  
3. Sets promoted properties of the copy of the original message depending upon the nature of the FIN response.  
  
4. Publishes the copy of the original message back to the MessageBox. Custom handlers can then subscribe to, retrieve, and handle the message as required.  
  
## Subscription to Outbound Messages  
 The FRR orchestration is directly bound to the MessageBox. The FRR orchestration subscribes to all outbound messages bound for the SWIFT network that do not contain validation errors, by subscribing to the following properties:  
  
- [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Failed==False (as set by the SWIFT Disassembler validation process)  
  
- [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Swiftbound==True (as set by the SWIFT Disassembler configuration process)  
  
## Message/Response Correlation  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] correlates the original outbound FIN message to the inbound FIN response message by comparing the following properties:  
  
- The MQMD_CorrelID context property of the FIN response  
  
- The [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRCorrelationToken property of the outbound MTXYY message. This property is promoted by the party-resolution stage of the receive pipeline.  
  
  The values of these properties must be identical. The encoder stage of the send pipeline for messages bound for SWIFT sets the MQMD_MsgID property of the outgoing message to the value of the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRCorrelationToken property. SAA sets the MQMD_CorrelID property of the response message to the value of MQMD_MsgID.  
  
## Setting of Promoted Properties  
 After receiving a FIN response and correlating it to the copy of the original message, the FRR orchestration sets the following promoted properties of the copy of the original message according to the nature of the response:  
  
- [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRFailed to True if the response was an ACK or False if the response was a NAK  
  
- [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRFailedReason to the one of the following values, if the response was a NAK:  
  
  -   *\<ErrorCode\>* (from the 405 field of the MTS21_FIN_ACKNAK negative-acknowledgment message)  
  
  -   TransportError (from an MQ Series PAN/NAN message)  
  
  -   DelayedNAK (from an MT015 (DNK) message)  
  
  -   AbortReceived (from an MT019 (Abort Notification) message)  
  
- [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRFailedReason to TimedOut if [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] did not receive a response within the timeout period. For more information about the FRR Delay Time-out, see the "Reconciliation Time-Out" section below or [Setting the FRR Delay Time-Out](../../adapters-and-accelerators/accelerator-swift/setting-the-frr-delay-time-out.md).  
  
- [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_SendingServiceType to [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrService  
  
- BTS.Operation to the value corresponding to the type of message response. For more information, see [Creating the FRR Send Ports for Sending to the Custom Handlers](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-ports-for-sending-to-the-custom-handlers.md).  
  
  - [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSendTransport for an MQ Series PAN/NAN message (MQ Series transport-level ACK/NAK)  
  
  - [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSend010NDW for an MT010 message (Non-Delivery Warning)  
  
  - [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSend011Delivered for an MT011 message (Delivery Notification)  
  
  - [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSend012SenderACK for an MT012 message (Sender Notification)  
  
  - [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSend015DNK for an MT015 message (DNK, or Delayed NAK)  
  
  - [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSend019Abort for an MT019 message (Abort Notification)  
  
  - [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSendS21ACK for an MTS21_FIN_ACKNAK acknowledgment message (ACK of a FIN message sent by an LT)  
  
  - [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSendS21NAK for an MTS21_FIN_ACKNAK negative-acknowledgment message (NAK of a FIN message sent by an LT)  
  
## Direct Binding  
 Receive inputs for the orchestration are defined by subscriptions that the orchestration makes to the MessageBox. Context properties and values promoted by the orchestration define the send outputs for a message that the orchestration publishes to the MessageBox. Because of this direct binding to the MessageBox, the orchestration is decoupled from the following:  
  
- The physical receive locations that receive outbound messages from the back-end application for routing to SAA  
  
- The send ports that send outbound FIN messages from [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] to the SWIFT Alliance Access (SAA)  
  
- The receive locations that receive incoming FIN response messages from SAA  
  
- The physical MQSeries queues where FIN responses are deposited by SAA  
  
## Reconciliation Time-Out  
 When [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] creates a new instance of the FRR orchestration, the orchestration starts waiting for FIN responses. At run time, you must configure the orchestration to time out after some duration, so that it will not wait for the response indefinitely. When the time-out duration expires, the FRR orchestration promotes the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRFailedReason property and sets it to TimedOut. It then publishes messages out to the MessageBox, and terminates. If you time out, the correlation ID is gone.  
  
 You can create a custom handler to process timed-out messages (the copy of the original outbound message). [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] would accomplish this by using a Listen shape in the orchestration. For more information, see [Setting the FRR Delay Time-Out](../../adapters-and-accelerators/accelerator-swift/setting-the-frr-delay-time-out.md).