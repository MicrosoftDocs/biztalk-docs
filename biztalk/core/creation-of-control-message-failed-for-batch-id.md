---
description: "Learn more about: Creation of Control Message failed for Batch id"
title: "Creation of Control Message failed for Batch id"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Creation of Control Message failed for Batch id
## Details  
  
|       Field     |                               Error Details                                            |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                               CreateControlMessageFailed                               |
|  Message Text   |                  Creation of Control Message failed for Batch id {0}.                  |
  
## Explanation  
 This Error/Warning/Information event indicates BizTalk Server was start/stop a batch.  
  
## User Action  
 To resolve this error, ensure that a batch with the given Id is present in the Agreement properties of the containing Agreement and the database is up.
