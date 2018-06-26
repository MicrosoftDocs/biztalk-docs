---
title: "Best Practices for Managing Certificates1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "best practices, certificates"
  - "certificates, security"
  - "security, certificates"
  - "certificates, best practices"
  - "best practices, security"
  - "security, best practices"
ms.assetid: cd182df4-0fcd-409c-9221-89f92e069f07
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Best Practices for Managing Certificates
This section provides best practices for managing certificates in your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.  
  
- **Do a Threat Model Analysis of your environment**  
  
   Do a Threat Model Analysis (TMA) of your environment to determine whether signing or encryption certificates will help you mitigate security threats.  
  
- **Create a plan for public key certificates with partners**  
  
   Create a plan for sending and receiving public key certificates with partners. If you are not using signing certificates for party resolution, the public certificate can be attached to the message, in which case you do not need a copy of the certificate in your system beforehand.  
  
- **Download the certificate revocation list at set intervals**  
  
   Download the certificate revocation list (CRL) from your certification authority (CA) at set intervals. We recommend doing this once a week. The CRLs are downloaded automatically if there is a CA for the domain in which the BizTalk servers are joined.  
  
- **Establish guidelines with partners for submitting public keys**  
  
   As part of your Service Level Agreement (SLA) with your partner, establish guidelines for submitting public keys, notifying you when their certificates are about to expire, and notifying you when they revoke a certificate.  
  
- **Verify signing certificates**  
  
   Make sure you verify the signing certificates against the certificate revocation list. For more information about how to verify the signing certificates, see [How to Configure the MIME-SMIME Decoder Pipeline Component](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md).  
  
- **Avoid denial of service attacks for digital signatures**  
  
   Determine what you want to do with messages when [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cannot validate the digital signature. Setting the **Authentication** property on the receive port will help prevent denial of service attacks.  
  
  > [!NOTE]
  >  The **Authentication - Drop messages** and **Authentication - Keep messages** flags on the receive port require that the Party Resolution pipeline component be configured correctly, and that the parties are defined in BizTalk Server. For more information about configuring the Party Resolution pipeline component, see [Party Resolution Pipeline Component](../core/party-resolution-pipeline-component.md).  
  
- **Create separate receive locations for encrypted and unencrypted messages**  
  
   If you plan to receive MIME-encrypted messages from some partners and unencrypted messages from other partners, create separate receive locations in different hosts for encrypted and unencrypted messages. When you expect only MIME-encrypted messages, configure the **Allow Non MIME Message** option in the Decode MIME/SMIME pipeline component to **No**.  
  
- **Manage certificates with partners**  
  
   Make certificate management part of your partner management practices. When you add or remove a party from the BizTalk Server environment, we recommend that you add or remove the certificates associated with that partner.  
  
- **Remove certificates before removing a host instance**  
  
   Before removing a host instance from a BizTalk server, remove the certificates in the personal store of the account under which the host instance is running.  
  
## See Also  
 [Managing BizTalk Server Security](../core/managing-biztalk-server-security.md)   
 [Best Practices for Managing Windows Groups and User Accounts](../core/best-practices-for-managing-windows-groups-and-user-accounts.md)