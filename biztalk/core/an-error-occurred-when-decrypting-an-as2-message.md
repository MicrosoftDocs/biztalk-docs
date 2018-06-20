---
title: "An error occurred when decrypting an AS2 message | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0bfb1d2a-c79d-4541-8a6d-bab0986f456b
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# An error occurred when decrypting an AS2 message
## Details  

|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       AS2 Engine                                       |
|  Symbolic Name  |                                           -                                            |
|  Message Text   |                   An error occurred when decrypting an AS2 message.                    |

## Explanation  
 This Error/Warning/Information event indicates that the AS2 Decoder component of the receive pipeline could not decrypt the AS2 message. This can occur if the certificate used in the decryption process is not valid, is not stored in the appropriate location, or does not match the certificate used in the encryption process.  

## User Action  
 To resolve this error, do one or more of the following:  

- Verify that the encryption wrapper in the AS2 message is valid. If not, determine why the message was encoded improperly by the encoder.  

- Verify that the public key used in the encryption process and the private key used in the decryption process match.  

- Verify that the Key Usage property of the certificate used for encryption and decryption is set to "data encipherment".  

- Verify that there is not a broken chain of intermediate certificate authorities. If there is, delete the old certificate, and create and use a new certificate.  

- Verify that the certificate has not timed out by checking its expiration date in the Certificates store (using MMC with a certificates snap-in.).  

- Verify that the certificate has not been revoked by checking the Certification Revocation List. (You can have BizTalk Server check this automatically by checking the Check Certification Revocation List property in the General AS2 properties in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.)  

- Verify that the certificate used for decryption is stored in the Current User\Personal store of each BizTalk server that hosts a MIME/SMIME decoder pipeline as each host instance service account.
