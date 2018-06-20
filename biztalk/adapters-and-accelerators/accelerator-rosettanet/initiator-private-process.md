---
title: "Initiator Private Process | Microsoft Docs"
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
  - "erros"
  - "LOBs"
  - "messages, message flow"
  - "private processes, initiator"
  - "private processes, message flow"
  - "private processes, errors"
ms.assetid: 8444a5c8-445a-4bbd-a793-a16816fcb397
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Initiator Private Process
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] uses the initiator private process (PrivateInitiator.odx) to process service content at an initiator computer. This includes the following:  
  
- Creating the service content of an original message and routing the message to the public process, in route to the trading partner  
  
- Processing a return signal message and routing it to the line-of-business (LOB) application  
  
- In the case of a double-action PIP, processing a response return message and routing it to the LOB application.  
  
  The private process also sets metadata and adds any attachments. The private process routes outgoing messages to the public process, which adds RosettaNet Implementation Framework (RNIF) headers and prepares the message for transmission. The private process routes incoming messages to the MessagesToLOB table in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] database, in route to the LOB application.  
  
  This private process automates the purchase query/purchase order processes that use 3A2 and 3A4 Partner Interface Processes (PIPs). It also handles any other PIP messages. You can customize the private process for your specific business processes.  
  
## Message Flow  
 The message flow through the initiator private process is as follows:  
  
1. The initiator private process receives the original message from the MessagesFromLOB table in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] database. The back-end LOB application routes the message to this table.  
  
2. The private process prepares the service content of an initiated message, and sends it to the public process.  
  
3. The initiator private process then enters a wait state, listening for a return signal.  
  
4. Upon receiving a return signal from the public process, the private process constructs a signal message, and sends the signal to the MessagesToLOB table in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] database, in route to the LOB application.  
  
5. The private process sends a notification to the LOB application that it put the signal message in the MessagesToLOB table.  
  
6. If the RNIF version is 1.1, the private process waits for an acceptance acknowledgement signal message. If it receives the signal, it constructs the signal message, and sends the signal to the MessagesToLOB table, in route to the LOB application.  
  
7. If the original message(s) was a single-action message, the private process is complete after it has returned the signal message to the LOB application. If the original message was a double-action message, the private process listens for a response message.  
  
8. If the private process receives a response message from the public process, it constructs a response message in the format of the LOB application. This involves getting the LOB message template, serializing the XML service content, and loading the XML message parts into the LOB message.  
  
9. The private process routes the message to the MessagesToLOB table in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] database.  
  
10. If the response message has an attachment, the private process calls the AttachmentHelper tool to process the attachment.  
  
11. The private process sends a notification to the LOB application that it put the response message in the MessagesToLOB table, and then is complete.  
  
## Handling of Incorrect Messages  
 When the initiator private process receives an incorrect message from the LOB application, the private process sends an exception message back to the LOB. However, the private process does not post the incorrect message in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] BizTalk Administration Console. Therefore, you are not able to view the incorrect message in BizTalk Administration Console. You can use the exception message to access the incorrect message to determine which message was incorrect, and then access the incorrect message in the MessagesFromLOB table of the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA database. However, this message may not be the same as the message that the private process consumed, because the stored process and adapter used to process the message edit it. They add a root element and namespace to the message. The stored process and adapter possibly return multiple records.  
  
## See Also  
 [Private Processes](../../adapters-and-accelerators/accelerator-rosettanet/private-processes.md)   
 [Responder Private Process](../../adapters-and-accelerators/accelerator-rosettanet/responder-private-process.md)   
 [Orchestration Samples](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md)   
 [PrivateInitiator Sample](../../adapters-and-accelerators/accelerator-rosettanet/privateinitiator-sample.md)