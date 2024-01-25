---
description: "Learn more about: Segment Exceeds Maximum Use Description"
title: "Segment Exceeds Maximum Use Description"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Segment Exceeds Maximum Use Description
## Details  
  
| Field | Error Details |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                         X12SegmentExceedsMaximumUseDescription                         |
|  Message Text   |                        Segment Exceeds Maximum Use Description                         |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the interchange contained more instances of a segment than allowed by the schema.  
  
## User Action  
 To resolve this error, make sure that the interchange does not have more than the maximum allowed number of segments, and then resend the interchange.
