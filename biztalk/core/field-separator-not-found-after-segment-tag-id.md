---
description: "Learn more about: Field separator not found after segment tag id"
title: "Field separator not found after segment tag id"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Field separator not found after segment tag id
## Details  
  
| Field | Error Details | 
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                          X12SeFsNotFoundAfterTagIdDescription                          |
|  Message Text   |                     Field separator not found after segment tag id                     |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive pipeline could not process the interchange because the interchange contained a segment that had a segment identifier without a data element separator immediately following it.  
  
## User Action  
 To resolve this error, ensure that all segment identifiers in the interchange have data element separators immediately following them, and then have the interchange resent.
