---
description: "Learn more about: Loop repeats less than the minimum allowed number of times"
title: "Loop repeats less than the minimum allowed number of times"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Loop repeats less than the minimum allowed number of times
## Details  
  
| Field | Error Details |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                          X12SeLoopRepeatsLessTimesDescription                          |
|  Message Text   |               Loop repeats less than the minimum allowed number of times               |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the interchange contained a loop that repeated fewer times than the minimum number of times required by the message schema.  
  
## User Action  
 To resolve this error, make sure that the loop repeats in the interchange at least the number of times in the minOccurs property specified for the loop in the message schema, and then have the interchange resent.
