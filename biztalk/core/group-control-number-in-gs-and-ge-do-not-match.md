---
description: "Learn more about: Group control number in GS and GE do not match"
title: "Group control number in GS and GE do not match"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Group control number in GS and GE do not match
## Details  
  
| Field | Error Details | 
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                         X12FaControlNumberMismatchDescription                          |
|  Message Text   |                     Group control number in GS and GE do not match                     |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive pipeline could not process the incoming X12 interchange because the control numbers contained in the GS06 and GE02 fields of the  interchange do not have the same value.  
  
## User Action  
 To resolve this error, make sure that the group control numbers contained in the GS06 and GE02 fields of the interchange have the same value, and then have the interchange resent.
