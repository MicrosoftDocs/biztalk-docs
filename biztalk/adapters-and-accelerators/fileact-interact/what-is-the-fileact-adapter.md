---
title: "What Is the FileAct Adapter? | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 05ec8f1e-57f9-4e2d-ab8b-22b5c4b28055
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# What Is the FileAct Adapter?
The FileAct adapter for SWIFTNet provides connectivity between BizTalk Server and the Society for Worldwide Interbank Financial Telecommunication (SWIFT) Secure IP Network (SIPN) for the transfer of files. The SIPN transfers messages and files over a secure private network which connects financial institutions, financial industry infrastructures, and customers. The FileAct adapter uses the SWIFTNet Link (SNL) application programming interface (API)s to connect to the SIPN.  
  
 The FileAct adapter provides a mechanism for SWIFT participants to securely and reliably exchange files and information pertaining to those files. It supports the following functionality:  
  
-   Sending files to a SWIFTNet User  
  
-   Retrieving files from a SWIFTNet User  
  
-   Delivery notification confirming file receipt by a receiver  
  
-   Abort of transfers in progress  
  
-   File transfer state monitoring  
  
-   Concurrent file transfers  
  
-   Assurance of data authenticity and integrity  
  
-   Confidentiality of file data in transit  
  
-   Non-repudiation of file transfers  
  
-   Time-stamping  
  
## The FileAct Service  
 The FileAct adapter for SWIFTNet provides secure and reliable transfer of files, such as batches of structured financial messages or large reports. Typical applications include repetitive credit transfers such as pension or salary payments, securities value-added information and reporting, and regulatory reporting. SWIFTNet FileAct offers a variety of messaging modes:  
  
- **Store-and-forward file transfer.** SWIFTNet FileAct’s store-and-forward capability removes the uncertainty and inconvenience of worrying about whether or not your correspondents are online at the time you transmit the file. The file is delivered as soon as the recipient is ready to receive it. As a result, it provides an ideal way to send files to large numbers of correspondents, some of which may be in different time zones.  
  
- **Real-time file transfer.** Real-time messaging offers a lower-cost alternative to store and forward for files that are destined for correspondents that are online at the time of transmission. As a result it is ideal for sending files to a few large correspondents or market infrastructures.  
  
- **Real-time file retrieval.** This is an interactive service typically used to retrieve files in the context of workstation-based systems and often in conjunction with SWIFTNet Browse. We will support this mode.  
  
  The optional SWIFTNet FileAct features (on a file by file basis) include:  
  
- **Message priority.** File transfers can be flagged as “Urgent” in the message, to allow for appropriate processing by your correspondents.  
  
- **Delivery notification (real-time and store-and-forward modes).** Provides confirmation that your correspondent received your file.  
  
- **Non-repudiation of emission and reception.** In case of dispute, allows SWIFT to confirm that the file transfer did take place as claimed.  
  
  The standard SWIFTNet FileAct features include SWIFTNet PKI security<strong>.</strong> SWIFTNet FileAct is secured with SWIFTNet PKI and offers message authentication and integrity control.  
  
  All messages and files exchanged on SWIFTNet undergo a common set of checks to ensure that no user can bypass the security, validation and routing rules of the platform. These checks are performed by the SWIFTAlliance Gateway (SAG) application.  
  
## See Also  
 [Getting Started with the FileAct and InterAct Adapters](../../adapters-and-accelerators/fileact-interact/getting-started-with-the-fileact-and-interact-adapters.md)   
 [What Is SWIFTNet?](../../adapters-and-accelerators/fileact-interact/what-is-swiftnet.md)   
 [What Is the InterAct Adapter?](../../adapters-and-accelerators/fileact-interact/what-is-the-interact-adapter.md)