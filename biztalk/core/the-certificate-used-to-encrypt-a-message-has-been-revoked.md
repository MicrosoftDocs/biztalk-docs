---
title: "The certificate used to encrypt a message has been revoked | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 76c90690-002a-43bc-85f2-8aa5e7511ffa
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# The certificate used to encrypt a message has been revoked
## Details  
  
|                 |                                                                                         |
|-----------------|-----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]    |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                |
|    Event ID     |                                            -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI  |
|    Component    |                                       AS2 Engine                                        |
|  Symbolic Name  |                        EncryptionCertificateHasBeenRevokedError                         |
|  Message Text   | The certificate used to encrypt a message has been revoked. Certificate thumbprint: {0} |
  
## Explanation  
 This Error/Warning/Information event indicates that the send pipeline could not process the outgoing message because the certificate identified as the encryption certificate has been revoked.  
  
## User Action  
 To resolve this error, do one of the following:  
  
-   Have the receiver of the message create a new certificate and send the public key to you. Add the certificate to the Local computer\Other People certificate store, and then identify the certificate as the encryption certificate in the Certificate page of the Send Port Properties dialog box.  
  
-   Disable the revocation list check by opening the BizTalk Server Administration Console, opening the AS2 Properties dialog box for the party resolved for the outgoing message, clicking the General node, and then clearing the Check Certification Revocation List property.