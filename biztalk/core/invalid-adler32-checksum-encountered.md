---
description: "Learn more about: Invalid Adler32 checksum encountered"
title: "Invalid Adler32 checksum encountered"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Invalid Adler32 checksum encountered
## Details  
  
| Field | Error Details |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       AS2 Engine                                       |
|  Symbolic Name  |                     InvalidAdler32ChecksumInCompressedMessageError                     |
|  Message Text   |                          Invalid Adler32 checksum encountered                          |
  
## Explanation  
 This error refers to the ASN.1 structure of the compressed data. The error indicates the sender of the compressed data either structured the compressed data incorrectly or there was tampering (unauthorized change) of the message.  
  
## User Action  
 The use of **Invalid Adler32 checksum encountered** indicates a high probability of tampering. Check for tampering if you see **Invalid Adler32 checksum encountered**.
