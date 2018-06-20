---
title: "MLLP Send Adapter Processing | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MLLP-encoded messages, send adapters"
  - "send adapters"
  - "MLLP adapters, send adapters"
ms.assetid: b8e47c7f-4a69-4f0c-86b4-26ed9c70613c
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MLLP Send Adapter Processing
The Minimal Lower Layer Protocol (MLLP) send adapter supports one-way and two-way transport modes in the following configurations:  
  
-   Two-way solicit-response send adapter  
  
-   One-way send adapter configured to receive acknowledgments (ACKs)  
  
-   One-way send adapter configured for no return messages  
  
## Two-way solicit-response send MLLP adapter  
 Use this adapter in a true end-to-end synchronous scenario. As such, you can only use this adapter with one destination party. The send adapter will continuously maintain an open connection against the remote party (URL) until it routes a return message to the request response receive port. See the following diagram for the architecture of request response/solicit response processing.  
  
 When you use this adapter, you can direct the system to return either an ACK or a response message to the line-of-business application. You do so with the Route ACK to Send Pipeline on Request Response Receive Port setting in the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer. Select this property to return an ACK, or deselect it to return a response meeting.  
  
 Once a send port using this adapter has successfully sent the original message, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] deletes that message. The receive pipeline associated with this send port will not generate an ACK. BizTalk will forward the query response to the source application regardless of the value of the MSA2 field of that response.  
  
## One-way send MLLP adapter configured to receive ACKs  
 This adapter receives ACKs on the same socket connection that it sends the original message on, and delivers the ACKs to the receive location. The send adapter continuously maintains an open connection against the remote party (URL), even if no messages are waiting for [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] to send them to it. If several ports are pointing to the same remote party, the send adapter maintains one connection for each send port.  
  
 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) setup installs a default receive location, TwoWayAckReceiveLocation. You can use this receive location with the MLLP send adapter for receiving ACKs. This configuration of the send port using this adapter requires you to associate a receive location with the send port.  
  
 Use this send port if you are set up to receive a response message with an MSA field, or to support multiple destinations. The two-way solicit-response adapter does not work with the MSA field or with multiple destinations.  
  
### Acknowledgments received by the one-way MLLP send adapter  
 When a one-way MLLP send adapter configured for ACKs receives one, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] deletes the original message from the MessageBox database, retries it, or suspends it, depending on the type of the ACK. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] parses the ACK in two phases:  
  
- The first phase is done in the send adapter where [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] parses the field MSA1 to determine the type of the ACK.  
  
- In the second phase, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] performs a complete parsing of the ACK, and then submits the ACK to the MessageBox database.  
  
  You configure the ACK that the two-way send adapter expects in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer.  
  
  The following table shows the ACKs that an MLLP send adapter can receive and the resulting action on the original message.  
  
|ACK received|Action on the original message|  
|------------------|------------------------------------|  
|Commit Accept, or Application Accept|Delete from the MessageBox database|  
|Commit/Application, Reject ACK, or Invalid ACK|Suspend|  
|Commit/Application Error|Retry/Move to backup transport/Suspend|  
|Static ACK Success|Delete from the MessageBox database|  
|Static ACK Failure|Suspend|  
  
 The following table shows ACK conditions that are not valid.  
  
|Instance|Condition|  
|--------------|---------------|  
|HL7 (Original, Enhanced, Deferred)|1.  Does not contain XML.<br />2.  Does not have the structure so the MSA1 field cannot be retrieved; or the MSA1 field does not contain one of the permissible values (CA, AA, CR, AR, CE, AE).|  
|Static|Does not match one of the permissible values for success or fail ACK.|  
|Contains XML|Treated as an Acceptance ACK (regardless of the content) and deleting the original message.|  
  
### Error Conditions  
 The following can occur when there is an error condition or inactivity:  
  
- If the outgoing message fails in serialization, the send adapter will not send the message, unless it is a batch message that [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] is streaming. If that is the case, and [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] detects a serialization failure halfway through the message, the adapter will not send EB/CR since [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] has not sent the complete message. The pipeline logs an error, and the adapter tries to send the batch message again.  
  
- If a send operation fails, the adapter tries to send the message again, up to the number of retries specified in the send-port configuration settings. After exhausting the retries, the message moves to the backup transport, if one exists. If all else fails, the message is suspended. The suspended message will be in the original (XML) form.  
  
  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] can generate the following events to describe the error conditions:  
  
|        Event        |  ID  |                                                                                                                                   Error Condition                                                                                                                                   |
|---------------------|------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ErrorSendingMessage | 8450 | Could not send a message to the remote party. The most common reasons are network failures or timeouts. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] may report this error if the send pipeline fails while serializing a large message. |
|  ErrorReceivingAck  | 8451 |                                                                                                       Could not receive an acknowledgment, due to network failure or timeout.                                                                                                       |
|   ErrorConnecting   | 8453 |                                                    Could not establish a TCP connect to the remote party—the host name could not be resolved, or the remote party is not listening on the port or is rejecting the connections.                                                     |
  
> [!NOTE]
>  The configuration of the destination party (in MSH5 of the original message) determines whether [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] expects an HL7 or static ACK. In case of a mismatch, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] treats the ACK as not valid.  
  
 After the MLLP send adapter processes an ACK, the ACK is delivered to the receive location as a message on its own. The disassembler performs full parsing of the ACK, which may result in parsing errors being reported by the receive pipeline and/or the ACK being suspended.  
  
## See Also  
 [Processing MLLP-encoded Messages](../../adapters-and-accelerators/accelerator-hl7/processing-mllp-encoded-messages.md)   
 [Configuration Parameters for Send and Receive Adapters](../../adapters-and-accelerators/accelerator-hl7/configuration-parameters-for-send-and-receive-adapters.md)   
 [MLLP Receive Adapter Processing](../../adapters-and-accelerators/accelerator-hl7/mllp-receive-adapter-processing.md)   
 [Setting Up a Send Port for Receiving ACKs](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md)