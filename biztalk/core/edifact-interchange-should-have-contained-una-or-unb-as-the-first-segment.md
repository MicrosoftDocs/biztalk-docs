---
description: "Learn more about: Edifact interchange should have contained UNA or UNB as the first segment"
title: "Edifact interchange should have contained UNA or UNB as the first segment"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Edifact interchange should have contained UNA or UNB as the first segment
## Details  
  
|     Field       |                              Error Details                                                       |
|-----------------|--------------------------------------------------------------------------------------------------|
|  Product Name   |        [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]        |
| Product Version |                    [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                    |
|    Event ID     |                                                -                                                 |
|  Event Source   |      [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI      |
|    Component    |                                            EDI Engine                                            |
|  Symbolic Name  |                                                -                                                 |
|  Message Text   | Edifact interchange should have contained UNA or UNB as the first segment. Instead {0} was found |
  
## Explanation  
 This Error/Warning/Information event indicates that the EDI receive pipeline could not process the incoming EDIFACT interchange because the first segment was neither a UNA nor a UNB segment. The UNA segment is optional; the UNB segment is mandatory.  
  
## User Action  
 To resolve this error, ensure that the sender of the interchange includes the UNA or UNB segment as the first segment of the interchange, and then resends the interchange.
