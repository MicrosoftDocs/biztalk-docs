---
description: "Learn more about: Error encountered in reading delimiters from ISA data"
title: "Error encountered in reading delimiters from ISA data"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Error encountered in reading delimiters from ISA data
## Details  
  
|      Field      |                             Error Details                                              |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                                     InvalidIsaData                                     |
|  Message Text   |                 Error encountered in reading delimiters from ISA data                  |
  
## Explanation  
 This Error/Warning/Information event indicates that the EDI receive pipeline encountered an error when processing an incoming X12 interchange because it could not parse the separators from the ISA segment.  
  
## User Action  
 To resolve this error, verify that the separators in the ISA segment of the incoming interchange are unique and valid. If not, have the sender of the interchange enter unique and valid values into each of the separator fields (the ISA11 segment for the repetition separator and the ISA16 segment for the component separator), and then resend the interchange.
