---
title: "A4SWIFT Security Features for Message Repair and New Submission | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "security, messages"
  - "A4SWIFT, security"
  - "security, A4SWIFT"
  - "messages, security"
ms.assetid: c34bcba7-fecd-4e2f-ab49-a6ccfd96198b
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# A4SWIFT Security Features for Message Repair and New Submission
[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] provides out-of-the-box facilities for SWIFT message creation, repair, rekey verification, and approval. Business users create, edit, and review SWIFT messages by using [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)][!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)], which provides a graphical representation and user interface for financial (FIN) messages. [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] renders the entry/repair/rekey verification form from the XML produced by the A4SWIFT runtime and [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. A4SWIFT provides an [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] template for each FIN message type (based on the corresponding A4SWIFT XSD schema) so that you can open any SWIFT FIN message types in [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]. A4SWIFT provides the following features to aid in security.  
  
## InfoPath Forms  
 Through the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forms generated with the FormGenerator Utility provided by A4SWIFT, business users submit and retrieve SWIFT messages to and from inboxes and outboxes implemented on secure Windows SharePoint Services Web folders. [!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)] Web folder security is provided completely by [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)] using file-system access control lists (ACLs), [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Authentication, and Internet Information Services (IIS) security features. Data is protected while "on the wire" between [!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)] Web folders and [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] by Secure Sockets Layer (SSL) and HTTPS transport protocols.  
  
 A4SWIFT [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forms are created as "untrusted." This status provides the highest level of security. For more information about trusted and untrusted, see [InfoPath Security](../../adapters-and-accelerators/accelerator-swift/infopath-security.md).  
  
## Runtime Service  
 A4SWIFT provides a runtime service (implemented as a BizTalk orchestration) to authenticate, validate, process, and route SWIFT messages between the SharePoint Web folders, message repair/entry orchestrations, back-end systems, and ultimately, to the SWIFT network. This runtime service is known as A4SWIFT Message Repair and New Submission.  
  
## Secure Messages  
 The storage and delivery of SWIFT messages between [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)], [!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)], and Message Repair and New Submission is secured by underlying services ([!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)], IIS, [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]) and transport protocols (SSL, HTTPS). However, the message creation, repair, approval, and submission infrastructure made up of Message Repair and New Submission, [!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)], and [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] requires additional user-level security to enforce authenticity and protection of SWIFT messages handled by end users.  
  
 A4SWIFT also defines and implements user-level security semantics to make sure that SWIFT messages are modified and submitted only by trusted and authorized users, and that message data is not altered or tampered with during the asynchronous steps of the submission process (for example, while messages are sitting in a SharePoint Web folder waiting for user intervention). Coordinated and choreographed security features on the workstation (through [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]) and server (through A4SWIFT Message Repair and New Submission) enforce these user-level security policies.