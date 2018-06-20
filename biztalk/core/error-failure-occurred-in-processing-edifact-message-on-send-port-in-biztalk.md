---
title: "A failure occurred in processing Edifact message on send port: No agreement for receiver and sender identifier-qualifier pairs | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cffc4705-164f-4779-8f04-c6a2a7f1bbda
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# A failure occurred in processing Edifact message on send port: No agreement for receiver and sender identifier-qualifier pairs
## Details  
  
|                 |                                                                                                                                                                   |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                        [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                         |
| Product Version |                                                    [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                     |
|    Event ID     |                                                                                 -                                                                                 |
|  Event Source   |                                      [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                       |
|    Component    |                                                                            EDI Engine                                                                             |
|  Symbolic Name  |                                                                                 -                                                                                 |
|  Message Text   | A failure occurred in processing Edifact message on send port {0}. No agreement exists for receiver and sender identifier/qualifier pairs for {1}, {2}, {3}, {4}. |
  
## Explanation  
 This Error/Warning/Information event indicates BizTalk Server was unable to resolve the party for the EDIFACT interchange because it was unable to match promoted sender qualifier and identifier properties, and promoted receiver qualifier and identifier properties, with the corresponding values for a party.  
  
## User Action  
 To resolve this error, ensure that the sender qualifier and identifier (UNB2.1 and UNB2.2) and receiver qualifier and identifier (UNB3.1 and UNB3.2) defined in the party's UNB Segment Definition page of the EDI Properties dialog box match the corresponding promoted properties in the context of the interchange.