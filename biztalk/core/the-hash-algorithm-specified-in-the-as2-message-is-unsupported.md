---
description: "Learn more about: The hash algorithm specified in the AS2 message is unsupported"
title: "The hash algorithm specified in the AS2 message is unsupported"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# The hash algorithm specified in the AS2 message is unsupported
## Details  
  
| Field | Error Details |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       AS2 Engine                                       |
|  Symbolic Name  |                            UnsupportedAS2HashAlgorithmError                            |
|  Message Text   |            The hash algorithm specified in the AS2 message is unsupported.             |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive pipeline could not generate the MDN as specified because the MIC hash algorithm specified in the signed-receipt-micalg header of the received AS2 message is not a valid value.  
  
## User Action  
 To resolve this error, have the sender of the message change the algorithm to either MD5 or SHA1, and resend the message.
