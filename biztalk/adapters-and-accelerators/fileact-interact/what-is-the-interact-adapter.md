---
title: "What Is the InterAct Adapter? | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a09063df-c6c4-41b9-96a1-e5059777fa72
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# What Is the InterAct Adapter?
The InterAct Adapter for SWIFTNet provides connectivity between BizTalk Server and the SWIFT Secure IP Network (SIPN) for the transfer of messages. The SIPN transfers messages and files over a secure private network which interconnects financial institutions, financial industry infrastructures, and customers. The InterAct adapter uses the SWIFTNet Link (SNL) application programming interface (API)s to connect to the SIPN.  
  
 SWIFTNet InterAct provides secure and reliable exchange of individual structured financial messages. SWIFT customers’ messaging requirements vary from customer to customer but also from message to message.  
  
 It supports the following functionality:  
  
- PKI security  
  
- Message validation  
  
- Configurable central routing  
  
- Message priority  
  
- Delivery notification for store and forward messages  
  
- Non-repudiation of emission and receipt.  
  
  You use the InterAct Adapter for SWIFTNet with externally supplied applications to utilize the features of InterAct. This adapter has no knowledge of the contents of the messages to be transferred, and will not audit nor validate the contents of the messages, except for the exchange primitives.  
  
## InterAct Message Exchange  
 SWIFTNet InterAct provides secure and reliable exchange of individual structured financial messages. SWIFT customers’ messaging requirements vary from customer to customer but also from message to message. SWIFTNet InterAct offers you a broad range of telecommunication modes:  
  
- **Store-and-forward messaging.** SWIFTNet InterAct’s store-and-forward capability is designed for messages destined for a large number of correspondents, many of whom may not be online at the time of transmission. It removes the uncertainty and inconvenience of worrying about whether or not your correspondents are on-line at the time you send the message. The message is delivered as soon as the recipient is ready to receive it. As a result, it provides an ideal way to send individual instructions, confirmations and reports to large numbers of correspondents, some of which may be in different time zones.  
  
- **Real-time messaging.** Real-time messaging offers a low-cost alternative to store and forward for messages which are destined for correspondents that are online at the time of transmission. As a result, it is ideal for sending individual instructions, confirmations and reports, to a few large correspondents or for messages to market infrastructures.  
  
  The optional SWIFTNet InterAct features (on a message by message basis) include:  
  
- **Message priority.** Messages can be flagged as “Urgent” in the message, to allow for appropriate processing by your correspondents.  
  
- **Delivery notification (store-and-forward mode).** Provides confirmation that your correspondent received your message  
  
- **Non-repudiation of emission and reception.** In case of dispute, allows SWIFT to confirm that the message exchange did take place as claimed.  
  
  The standard SWIFTNet InterAct features include SWIFTNet PKI security. SWIFTNet FileAct is secured with SWIFTNet PKI and offers message authentication and integrity control.  
  
  All messages and files exchanged on SWIFTNet undergo a common set of checks to ensure that no user can bypass the security, validation and routing rules of the platform. These checks are performed by the SWIFTAlliance Gateway (SAG) application.  
  
## See Also  
 [Getting Started with the FileAct and InterAct Adapters](../../adapters-and-accelerators/fileact-interact/getting-started-with-the-fileact-and-interact-adapters.md)   
 [What Is SWIFTNet?](../../adapters-and-accelerators/fileact-interact/what-is-swiftnet.md)   
 [What Is the FileAct Adapter?](../../adapters-and-accelerators/fileact-interact/what-is-the-fileact-adapter.md)