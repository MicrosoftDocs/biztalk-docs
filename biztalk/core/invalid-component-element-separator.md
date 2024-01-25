---
description: "Learn more about: Invalid Component Element Separator"
title: "Invalid Component Element Separator"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Invalid Component Element Separator
## Details  
  
| Field | Error Details |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                   X12Ta1InvalidComponentElementSeparatorDescription\                   |
|  Message Text   |                          Invalid Component Element Separator                           |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the value of the component separator in the interchange was not limited to the characters in the ASCII character set. In X12, the segment terminator is the ISA16 field. In EDIFACT, the segment terminator is the UNA1 field.  
  
## User Action  
 To resolve this error, make sure that the segment terminator (the ISA16 field in an X12 interchange or the UNA1 field in an EDIFACT interchange) is limited to the characters in the ASCII character set. Have the interchange resent.
