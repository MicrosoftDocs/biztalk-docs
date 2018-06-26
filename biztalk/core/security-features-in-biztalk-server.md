---
title: "Security Features in BizTalk Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BizTalk Server, security"
  - "Master Secret server, security"
  - "security, Master Secret server"
  - "security, runtime"
  - "security, data"
  - "deploying, security"
  - "security, configuring"
  - "runtime, security"
  - "security, security features"
  - "security, messages"
  - "security, access control"
  - "security, about security"
  - "access control"
  - "security, deploying"
  - "data, security"
  - "messages, security"
ms.assetid: 5ab15023-fa71-439e-b3aa-420fe28806fa
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Security Features in BizTalk Server
Microsoft® BizTalk® Server provides a standard gateway for sending and receiving documents both within an intranet and through the Internet. Due to the possible business-critical nature of the messages sent to and from BizTalk Server, it is important to consider measures to help secure these messages and the information they contain both as they are in transit and while BizTalk Server processes and stores them. This section provides information about the BizTalk Server security features, and how you can use them to help secure your data and environment.  
  
 BizTalk Server uses the following measures to help secure inbound and outbound messages, to help secure the runtime and configuration information, and to help integrate securely with other applications and systems:  
  
 **Message security**  
  
- Authenticating the sender of a message. BizTalk Server can authenticate the sender of a message (either by using the certificate information or Windows integrated Security) in order to validate the identity of the sender of the message. For more information, see [Inbound Message Authentication](../core/inbound-message-authentication.md).  
  
- Authorizing of the receiver of a message. After BizTalk Server receives the message, BizTalk Server can determine what processes and users have permissions to receive the message. For more information, see [Authorizing the Receiver of a Message](../core/authorizing-the-receiver-of-a-message.md).  
  
  **Runtime and configuration security**  
  
- **Access control and securing data.** BizTalk Server uses access control to ensure that BizTalk Server processes have appropriate limits and that access to business critical information is controlled. In other words, BizTalk Server ensures that users and accounts have the least user rights possible to enable them to do their tasks. For more information, see [Access Control and Data Security](../core/access-control-and-data-security.md).  
  
  **Integrated security**  
  
- Enterprise Single Sign-On. BizTalk Server uses Enterprise Single Sign-On (SSO) to ensure that it encrypts the sensitive configuration information that the adapters, send, and receive locations require, thus helping to ensure that BizTalk Server stores and transmit this information in a secure manner. For more information, see [Using SSO](../core/using-sso.md).  
  
## See Also  
 [Designing the System Architectures for BizTalk Server](../core/designing-the-system-architectures-for-biztalk-server.md)   
 [Implementing Enterprise Single Sign-On](../core/implementing-enterprise-single-sign-on.md)   
 [Planning Message Security](../core/planning-message-security.md)   
 [Access Control and Data Security](../core/access-control-and-data-security.md)   
