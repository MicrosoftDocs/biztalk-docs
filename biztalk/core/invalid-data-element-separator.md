---
description: "Learn more about: Invalid Data Element Separator"
title: "Invalid Data Element Separator"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Invalid Data Element Separator
## Details  
  
| Field | Error Details |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                      X12Ta1InvalidDataElementSeparatorDescription                      |
|  Message Text   |                             Invalid Data Element Separator                             |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the value of the segment terminator in the interchange was not limited to the characters in the ASCII character set. In X12, the segment terminator is defined as the fourth character in the ISA segment. In EDIFACT, the segment terminator is the UNA2 field.  
  
## User Action  
 To resolve this error, make sure that the segment terminator (the fourth character of the ISA segment in an X12 interchange or the UNA2 field in an EDIFACT interchange) is limited to the characters in the ASCII character set. Have the interchange resent.
