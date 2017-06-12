---
title: "SWIFT Receive Adapter Store and Forward | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 11eeb335-366b-4b29-9078-de9396b258ca
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SWIFT Receive Adapter Store and Forward
The receive adapter receives messages from the SWIFT store and forward (SnF) queue. To receive messages from the queue, the adapter must open a session with the SnF queue. To open the queue, it must have a dedicated client process that establishes the session with the queue. In the design, this process is implemented as a COM plus out-of-proc component.  
  
## Push session store and forward sequence  
 The following list describes the store and forward sequence.  
  
1.  Start the server application that processes the messages.  
  
2.  The server process opens the required security contexts during the first SwCallback with the Sw:HandleInitRequest as an input primitive.  
  
3.  The server responds to the Sw:HandleInitRequest with either or both Sw:CryptoMode and Sw:FACryptoMode set to Advanced.  
  
     The server is now ready to start processing incoming requests.  
  
4.  To start the delivery of messages from a queue, a client process starts a push session. Based on the adapter configuration (push mode), the receive adapter spawns a client process called SnFQueueManager.exe to acquire the queue in push mode.  
  
5.  An SwCall() runs with Sw:AcquireSnFRequest (within the Sw:ExchangeSnFRequest) as an input primitive. This request starts a session with the queue indicated (if the SwSec:AuthorisationContext has the required RBAC role).  
  
6.  Immediately after responding with “Accepted” in the Sw:AcquireStatus, SWIFTNet SnF starts sending messages to the server as specified in the acquire. If the receive adapter was not yet started, messages get exceptions. (That is why it is important to have the receive adapters already started).  
  
7.  SWIFTNet SnF starts pushing a number of messages (up to the window size).  
  
8.  For every message acknowledged, a new message (if any) is pushed.  
  
9. The client process (SnFQueueManager.exe) has done its job and can now terminate. The process issues SwSec:DestroyContextRequest, which cleans up the open security contexts. After the Sw:TermRequest, the process exits.  
  
### Message Correlation  
 The RequestRef field is preserved and substituted back in the response messages by the receive adapter. This ensures end to end correlation between the incoming message and the response message  
  
### Duplicate processing  
 If receiving a FileAct request, and the adapter instance receives a message with a Possible Duplicate Indicator node, then it must check to see if the referenced transfer has already completed successfully or if it has failed, and take the appropriate action. If the file transfer has already taken place then the adapter updates the transfer status as “Duplicate” otherwise it updates it as “Accepted.”  
  
### Acknowledgments  
 If the sender requests an acknowledgement for a FileAct request, the adapter checks for the file transfer completion event and generates the acknowledgement after verifying the file digest value. The adapter sends the acknowledgement message to BizTalk for the send adapter to pick it up and send it to the sender.  
  
## See Also  
 [SWIFT Receive Adapter Architecture](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-architecture.md)   
 [SWIFT Receive Adapter URI](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-uri.md)   
 [SWIFT Receive Adapter Initialization](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-initialization.md)   
 [SWIFT Receive Adapter Security Context](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-security-context.md)   
 [SWIFT Receive Adapter Synchronous and Deferred Modes](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-synchronous-and-deferred-modes.md)