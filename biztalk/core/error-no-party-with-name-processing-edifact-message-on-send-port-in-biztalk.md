---
title: "A failure occurred in processing Edifact message on send port: No Party with name | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 678baacb-1f21-4081-b788-ef346c3598ca
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# A failure occurred in processing Edifact message on send port: No Party with name
## Details  
  
|                 |                                                                                                   |
|-----------------|---------------------------------------------------------------------------------------------------|
|  Product Name   |        [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]         |
| Product Version |                    [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                     |
|    Event ID     |                                                 -                                                 |
|  Event Source   |                                        BizTalk Server EDI                                         |
|    Component    |                                            EDI Engine                                             |
|  Symbolic Name  |                                                 -                                                 |
|  Message Text   | A failure occurred in processing Edifact message on send port {0}. No Party exists with name {1}. |
  
## Explanation  
 This Error/Warning/Information event indicates that BizTalk Server was unable to resolve the party for the EDIFACT interchange because BizTalk Server was unable to match the send port that subscribed to the interchange with the send port associated with a party. This occurs if neither the DestinationPartyName property nor the sender qualifier and identifier and receiver qualifier and identifier properties are promoted, so are unavailable for send-side party resolution.  
  
## User Action  
 To resolve this error, ensure that the send port that subscribed to the interchange matches the send port associated with a party.