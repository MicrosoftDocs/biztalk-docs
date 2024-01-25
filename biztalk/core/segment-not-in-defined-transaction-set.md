---
description: "Learn more about: Segment Not In Defined Transaction set"
title: "Segment Not In Defined Transaction set"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Segment Not In Defined Transaction set
## Details  
  
| Field | Error Details |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                          X12SegmentNotInDefinedTSDescription                           |
|  Message Text   |                         Segment Not In Defined Transaction set                         |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive pipeline could not process the incoming X12 interchange because a transaction set in that interchange does not contain a segment required by the document schema.  
  
## User Action  
 To resolve this error, have the sender of the interchange add the required segment to the transaction set in the interchange, and then resend the interchange.
