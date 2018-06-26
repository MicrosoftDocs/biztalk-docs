---
title: "BizTalk Server Security Features | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "authentication"
  - "security, authentication"
  - "security, BizTalk Server"
  - "security, security features"
  - "BizTalk Server, security features"
ms.assetid: db356439-1898-4c09-86de-458a9bd21b18
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BizTalk Server Security Features
Financial Services applications and integration solutions developed by using [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] are [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications and are secured by native [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] security features. [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications are typically made up of messaging functionality (message processing, transformation, routing) and workflow automation (business process automation, business rules and logic evaluation). [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] provides general messaging and workflow automation security. [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] provides additional security features specific to securing end-user message entry, repair, approval, and submission. For more information about [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]-specific security, see [A4SWIFT Security Features for Message Repair and New Submission](../../adapters-and-accelerators/accelerator-swift/a4swift-security-features-for-message-repair-and-new-submission.md).  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] is designed around a messaging event model (centered on the MessageBox database and publisher-subscriber design pattern) in which the messages and documents, as well as the processing components that interact with them, are based on XML and Web services technologies. To help protect the integrity of any system made up of information, participants, and processes, the following primary requirements guide security mechanisms:  
  
- **Protecting the privacy of system elements.** Protecting the privacy of communications in an open computing and networking environment is the function of encryption. [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] supports encrypted communications through public key infrastructure (PKI), Secure Multipurpose Internet Mail Extensions (S/MIME), and Secure Sockets Layer (SSL). To authenticate and enhance protection of the privacy of messages, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] makes extensive use of digital certificates (keys).  
  
   PKI is the set of Internet protocols that address the methodologies that promote secure exchange of keys, the procedures and hierarchy of authority for authenticating keys, and the algorithms deployed for these purposes.  
  
   [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] uses the S/MIME protocol to encrypt and decrypt messages sent and received in multi-step, multi-party processes, with Data Encryption Standard (DES), 3DES, and RC2 encryption algorithm support. For encrypted point-to-point communication between a Web client and a Web server, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] uses the SSL protocol.  
  
- **Authenticating information, participants, and processes.** To authenticate information, participants, and processes, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] relies on signing certificates, [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Authentication, and an extended implementation of [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Authentication in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] known as Enterprise Single Sign-On (SSO). Signing certificates are digital certificates (or keys) that identify two parties to each other in a messaging exchange. A signing certificate also determines if a message was tampered with in transit.  
  
   [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] can use stored public keys to decode digitally signed incoming messages, and can use private keys to sign outbound messages that it generates. SSO is the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] extension to [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Authentication that allows parties and messaging events that are engaged in multi-step [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] processes to authenticate themselves, at any step in the process, to any resource in the process, without requiring multiple logons.  
  
- **Authorizing resource usage.** Authorization is the allocation and management of usage rights to the resources of a system. The primary [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] authorization mechanisms are [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] Roles, [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Authentication, and the MessageBox database. [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] stores all incoming and outgoing messages in its MessageBox database, before sending them to an orchestration process and after the orchestration sends the messages to a send pipeline. Access to [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] databases and resources is assigned to administrators, users, and host accounts using [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] Roles.  
  
  The [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] security architecture is based on a robust set of mechanisms that are implemented throughout [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] using a variety of methodologies designed to increase security. The [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] components that incorporate the security mechanisms are send and receive adapters, pipelines, the MessageBox database, orchestrations, and message security context properties.  
  
  These components use Authentication Required pipelines, multiple logical hosts and their "Authentication Trusted" property, and the Publish and Subscribe/Receive Authorization methodologies to deploy the security mechanisms. This multifaceted security architecture of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] provides numerous options for helping to design and execute more secure Financial Services messaging and workflow automation applications.