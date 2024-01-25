---
description: "Learn more about: One or more segments in error"
title: "One or more segments in error"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# One or more segments in error
## Details  
  
| Field | Error Details|
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                        X12TsOneOrMoreSegmentsInErrorDescription                        |
|  Message Text   |                             One or more segments in error                              |
  
## Explanation  
 This Error/Warning/Information event indicates that one or more segments in the interchange did not conform to the schema governing them.  
  
## User Action  
 To resolve this error, determine which segment is in error, open the schema governing that segment, and determine from that schema why the segment is in error.
