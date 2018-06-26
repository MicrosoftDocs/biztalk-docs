---
title: "Edifact interchange Xml serialization failed due to invalid structure, no transactionSet or UNE | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3ce1c219-f2ed-46c1-ae4b-8a4206f7cd01
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Edifact interchange Xml serialization failed due to invalid structure, no transactionSet or UNE
## Details  
  
|                 |                                                                                                                         |
|-----------------|-------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                    |
| Product Version |                               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                |
|    Event ID     |                                                            -                                                            |
|  Event Source   |                 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                  |
|    Component    |                                                       EDI Engine                                                        |
|  Symbolic Name  |                                            EfactTransactionSetOrUneNotFound                                             |
|  Message Text   | Edifact interchange Xml serialization failed due to invalid structure. Looking for TransactionSet or UNE, but not found |
  
## Explanation  
 This Error/Warning/Information event indicates that the EDI receive pipeline could not process the incoming EDIFACT interchange because the first segment was neither a UNA or a UNB segment. The UNA segment is optional; the UNB segment is mandatory.  
  
## User Action  
 To resolve this error, ensure that the sender of the interchange structures the message such that a transaction set in a group is either followed by another transaction set or a UNE segment. Have the sender then resend the interchange.