---
title: "A persistence exception has occurred during the batch submission in the batching Orchestration"
description: Persistence exception error message and resolution when using EDI batching in BizTalk Server.
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# A persistence exception has occurred during the batch submission in the batching Orchestration

## Details  
  
| Catetgory | Information |
|---|---|
|  Product Name   |  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| Product Version |  [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)] |
|    Event ID     | |
|  Event Source   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI   |
|    Component    |  Batching Engine  |
|  Symbolic Name  |  PersistenceExceptionOccurred  |
|  Message Text   | A persistence exception has occurred during the batch submission in the batching Orchestration. Batch Id = {0}, ErrorMessage = {1}. Please check your send port subscriptions and fix them. |
  
## Explanation  
 This Error/Warning/Information event indicates that BizTalk Server could not send a batched interchange because no send port subscribed to the interchange.  
  
## User Action  
 To resolve this error, ensure that a send port subscribes to the batch by setting the following filter properties for the send port: EDI.DestinationPartyName = \<PartyName\>, EDI.BatchEncodingType = EDIFACT or X12, and EDI.ToBeBatched = False.
