---
title: "Transaction Set Trailer Missing | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 07753300-fe47-47a6-a947-6abec10c1c90
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Transaction Set Trailer Missing
## Details  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                             X12TsTrailerMissingDescription                             |
|  Message Text   |                            Transaction Set Trailer Missing                             |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive pipeline could not process the incoming transaction set or the send pipeline could not process the outgoing transaction set because the transaction set did not include the SE transaction set trailer (for X12 transaction sets) or the UNT message trailer (for EDIFACT transaction sets).  
  
## User Action  
 To resolve this error, have the sender of the transaction set add to the transaction set an SE transaction set trailer (for X12 transaction sets) or the UNT message trailer (for EDIFACT transaction sets), and then resend the transaction set.