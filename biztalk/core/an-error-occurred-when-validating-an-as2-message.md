---
title: "An error occurred when validating an AS2 message | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0cf97c63-2bff-4474-9cd8-f68634493dcc
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# An error occurred when validating an AS2 message
## Details  

|                 |                                                                                                                       |
|-----------------|-----------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                   |
| Product Version |                              [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                               |
|    Event ID     |                                                           -                                                           |
|  Event Source   |                [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                 |
|    Component    |                                                      AS2 Engine                                                       |
|  Symbolic Name  |                                                           -                                                           |
|  Message Text   | An error occurred when validating an AS2 message. Make sure the certificates used have not timed out or been revoked. |

## Explanation  
 This Error/Warning/Information event indicates that the AS2 receive pipeline or the AS2 send pipeline could not validate the AS2 message. This can occur if the certificate used in the signature verification process is not valid, is not stored in the appropriate location, or does not match the certificate used in the signing process.  

## User Action  
 To resolve this error, do one or more of the following:  

- Verify that the signature wrapper in the AS2 message is valid. If not, determine why the message was signed improperly by the encoder.  

- Verify that the private key used in the signing process and the public key used in the signature verification process match.  

- Verify that the Key Usage property of the certificate used for signing and signature verification is set to "data encipherment".  

- Verify that there is not a broken chain of intermediate certificate authorities. If there is, delete the old certificate, and create and use a new certificate.  

- Verify that the certificate has not timed out by checking its expiration date in the Certificates store (using MMC with a certificates snap-in.).  

- Verify that the certificate has not been revoked by checking the Certification Revocation List. (You can have BizTalk Server check this automatically by checking the Check Certification Revocation List property in the General AS2 properties in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.)  

- Verify that the certificate used for signature verification is stored in the Local computer/Other People store of each BizTalk server that hosts a MIME/SMIME decoder pipeline as each host instance service account.
