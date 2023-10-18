---
description: "Learn more about: Control Number in ISA and IEA do not match"
title: "Control Number in ISA and IEA do not match"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Control Number in ISA and IEA do not match
## Details  
  
|      Field      |                         Error Details                                                  |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       AS2 Engine                                       |
|  Symbolic Name  |                                           -                                            |
|  Message Text   |                       Control Number in ISA and IEA do not match                       |
  
## Explanation  
 This Error/Warning/Information event indicates that the AS2 receive pipeline could not process the incoming interchange because the interchange control numbers contained in the ISA13 and IEA02 fields of the interchange do not have the same value.  
  
## User Action  
 To resolve this error, make sure that the interchange control numbers contained in the ISA13 and IEA02 fields of the interchange have the same value, and then have the interchange resent.
