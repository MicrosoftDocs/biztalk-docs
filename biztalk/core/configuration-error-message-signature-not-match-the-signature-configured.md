---
title: "Configuration error. The message signature doesn&#39;t match the signature configured for this party | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7cea0016-12e8-4ee8-ac44-11024b5e74ef
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuration error. The message signature doesn&#39;t match the signature configured for this party
## Details  
  
|                 |                                                                                                                                                                                                            |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                             |
| Product Version |                                                                         [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                         |
|    Event ID     |                                                                                                     -                                                                                                      |
|  Event Source   |                                                           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                           |
|    Component    |                                                                                                 AS2 Engine                                                                                                 |
|  Symbolic Name  |                                                                                                     -                                                                                                      |
|  Message Text   | Configuration error. The message signature doesn't match the signature configured for this party. Contact the sending partner and verify the certificate used. AS2-From:"{0}" AS2-To:"{1}" MessageID:"{2}" |
  
## Explanation  
 This Error/Warning/Information event indicates that the AS2 receive pipeline could not verify the signature when performing MIME processing. This could result from using a different certificate to process the received message than the sender used to sign the message. This can occur if BizTalk Server uses the settings of the wrong party to verify the signature of the incoming AS2 message.  
  
## User Action  
 To resolve this error, do one or more of the following:  
  
-   Ensure that the correct party is determined by the party resolution process for the incoming AS2 message. Do so by verifying that the correct party is resolved when BizTalk Server attempts to find a match between the AS2-From header in the incoming message and the value for EDIINT-AS2 From in the Aliases list in the General page of the Party Properties dialog box. If that does not resolve the party, verify that the correct party is resolved when BizTalk Server attempts to find a match between the AS2-From context property that is set for the incoming message and the name of a party.  
  
-   Ensure that the certificate defined in the Certificate page of the Party Properties dialog box, and stored in the Local computer\Other People store, corresponds to the certificate used to sign the message.