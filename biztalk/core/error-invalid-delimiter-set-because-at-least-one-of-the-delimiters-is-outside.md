---
description: "Learn more about: Invalid delimiter set because at least one of the delimiters is outside the allowed range"
title: "Invalid delimiter set because at least one of the delimiters is outside the allowed range"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Invalid delimiter set because at least one of the delimiters is outside the allowed range
## Details  
  
| Field | Error Details |
|-----------------|--------------------------------------------------------------------------------------------------------|
|  Product Name   |           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]           |
| Product Version |                       [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                       |
|    Event ID     |                                                   -                                                    |
|  Event Source   |         [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI         |
|    Component    |                                               EDI Engine                                               |
|  Symbolic Name  |                                          DelimiterOutOfRange                                           |
|  Message Text   | Invalid delimiter set {0}, at least one of the delimiters is outside the allowed range of 0 through 127 |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because one or more separators in the interchange was outside the range of values in the ASCII character set.  
  
## User Action  
 To resolve this error, make sure that each separator in the interchange is in the ASCII character set, and then have the interchange resent.
