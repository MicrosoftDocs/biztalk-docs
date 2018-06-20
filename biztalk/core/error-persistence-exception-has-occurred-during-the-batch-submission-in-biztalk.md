---
title: "A persistence exception has occurred during the batch submission in the batching Orchestration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cf6e832f-9d01-46e7-aaf5-2b402d509fac
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# A persistence exception has occurred during the batch submission in the batching Orchestration
## Details  
  
|                 |                                                                                                                                                                                            |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                     [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                     |
| Product Version |                                                                 [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                 |
|    Event ID     |                                                                                             -                                                                                              |
|  Event Source   |                                                   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                   |
|    Component    |                                                                                      Batching Engine                                                                                       |
|  Symbolic Name  |                                                                                PersistenceExceptionOccured                                                                                 |
|  Message Text   | A persistence exception has occured during the batch submission in the batching Orchestration. Batch Id = {0}, ErrorMessage = {1}. Please check your send port subscriptions and fix them. |
  
## Explanation  
 This Error/Warning/Information event indicates that BizTalk Server could not send a batched interchange because no send port subscribed to the interchange.  
  
## User Action  
 To resolve this error, ensure that a send port subscribes to the batch by setting the following filter properties for the send port: EDI.DestinationPartyName = \<PartyName\>, EDI.BatchEncodingType = EDIFACT or X12, and EDI.ToBeBatched = False.