---
title: "The AS2 Decoder was unable to locate the Disposition-Notification-Options HTTP header | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6de4b9a6-17b2-4455-9dbd-a6bb69fac1d5
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# The AS2 Decoder was unable to locate the Disposition-Notification-Options HTTP header
## Details  
  
|                 |                                                                                                                             |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                     [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                      |
| Product Version |                                 [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                  |
|    Event ID     |                                                              -                                                              |
|  Event Source   |                   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                    |
|    Component    |                                                         AS2 Engine                                                          |
|  Symbolic Name  |                               AS2DecoderMissingDispositionNotificationOptionsHTTPHeaderError                                |
|  Message Text   | The AS2 Decoder was unable to locate the Disposition-Notification-Options HTTP header which is required for MDN generation. |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive pipeline could not generate the MDN because the incoming AS2 message did not include the Disposition-Notification-Options header that indicates whether the MDN must be signed and which MIC algorithm must be used.  
  
## User Action  
 To resolve this error, have the sender of the AS2 message include the Disposition-Notification-Options header in the message and then resend the message.