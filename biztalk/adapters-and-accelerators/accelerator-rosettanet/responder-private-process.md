---
title: "Responder Private Process | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "line-of-business applications (LOBs)"
  - "messages, private processes"
  - "LOBs"
  - "messages, message flow"
  - "private processes, responder"
  - "private processes, message flow"
ms.assetid: 69b58320-977c-44d2-a7d6-f986213aecf2
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Responder Private Process
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] uses the responder private process (PrivateResponder.odx) to process service content at a responder computer. This includes the following:  
  
- Routing an incoming message to the line-of-business (LOB) application  
  
- Creating the service content of a response message and routing the message to the public process, in route to the responder computer  
  
  The private process also sets metadata and adds any attachments to the response message. The private process routes outgoing messages to the responder public process, which adds RosettaNet Implementation Framework (RNIF) headers and prepares the message for transmission. The private process routes incoming messages to the MessagesToLOB table in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] database, in route to the LOB application.  
  
  The [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK includes two responder private process samples that you can customize for your specific business processes. The first is the PrivateResponder process sample that contains the code for the responder private process installed by [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]. For more information, see [PrivateResponder Sample](../../adapters-and-accelerators/accelerator-rosettanet/privateresponder-sample.md).  
  
  The second sample is the PIP3A4PrivateResponder private process sample that automates the purchase query/purchase order processes that use 3A2 and 3A4 Partner Interface Processes (PIPs). It also handles any other PIP messages. For more information, see [3A4 Private Responder Orchestration Using a Business Rule](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md).  
  
## Message Flow  
 The message flow through the responder private process is as follows:  
  
1. The responder private process receives the original incoming message from the responder public process, in route from the initiator computer.  
  
2. The private process constructs the LOB application message. This involves getting the LOB message template, serializing the XML service content, and loading the XML message parts into the LOB message.  
  
3. The private process routes the message to the MessagesFromLOB table in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] database, in route to the back-end LOB application.  
  
4. If the original message has an attachment, the private process calls the AttachmentHelper component to process the attachment.  
  
5. The private process sends a notification to the LOB application that it saved the response message in the MessagesToLOB table.  
  
6. If the message is a single-action message, the private process is complete.  
  
7. If the message is a double-action message, the private process listens for a response from the LOB application.  
  
8. When the private process receives the response from the LOB application, it constructs a response message, and sends the message to the public process.  
  
9. The private process waits for the signal from the public process. If it receives the signal, it constructs the LOB signal message and sends it to the LOB application. If the RNIF version is 1.1, the private process will listen for a second acknowledgement signal, and upon receiving it, will construct the LOB signal message and send it to the LOB application. The private process notifies the LOB application after sending each signal message.  
  
10. If the private process receives a Notification of Failure (NoF) message from the public process, in route from the initiator, the private process constructs a "[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]Exception" message, and sends it to the LOB application.  
  
## See Also  
 [Private Processes](../../adapters-and-accelerators/accelerator-rosettanet/private-processes.md)   
 [Initiator Private Process](../../adapters-and-accelerators/accelerator-rosettanet/initiator-private-process.md)   
 [Orchestration Samples](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md)   
 [PrivateResponder Sample](../../adapters-and-accelerators/accelerator-rosettanet/privateresponder-sample.md)