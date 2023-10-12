---
description: "Learn more about: Reading Batch Descriptions from database failed"
title: "Reading Batch Descriptions from database failed"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Reading Batch Descriptions from database failed
## Details  
  
| Field | Error Details |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                                 LoadBatchFiltersFailed                                 |
|  Message Text   |     Reading BatchDescriptions from database failed. Error: {0}. Stack Trace: {1}.      |
  
## Explanation  
 This Error/Warning/Information event indicates BizTalk Server was unable to load the filters specified for the configured batches to compare context properties of incoming messages.  
  
## User Action  
 To resolve this error, ensure that the Management database is up and can be connected.
