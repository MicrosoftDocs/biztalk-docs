---
description: "Learn more about: Could not find an Agreement corresponding to batch"
title: "Could not find an Agreement corresponding to batch"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Could not find an Agreement corresponding to batch
## Details  
  
|      Field      |                             Error Details                                              |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                               AgreementNotFoundForBatch                                |
|  Message Text   |                Could not find an Agreement corresponding to batch {0}.                 |
  
## Explanation  
 This Error/Warning/Information event indicates BizTalk Server was unable to find a Batch corresponding to this Id while trying to start/stop a batch or process a batch message.  
  
## User Action  
 To resolve this error, ensure that a batch with the given Id is present in the Agreement properties of the containing Agreement.
