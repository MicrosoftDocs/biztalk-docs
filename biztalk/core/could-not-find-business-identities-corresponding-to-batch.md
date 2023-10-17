---
description: "Learn more about: Could not find Business Identities corresponding to batch"
title: "Could not find Business Identities corresponding to batch"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Could not find Business Identities corresponding to batch
## Details  
  
|    Field        |                            Error Details                                               |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                               IdentitiesNotFoundForBatch                               |
|  Message Text   |             Could not find Business Identities corresponding to batch {0}.             |
  
## Explanation  
 This Error/Warning/Information event indicates BizTalk Server was not able to process a batch message because of insufficient data.  
  
## User Action  
 To resolve this error, ensure that a batch with the given Id is present in the Agreement properties of the containing Agreement and proper business identities are specified for the agreement.
