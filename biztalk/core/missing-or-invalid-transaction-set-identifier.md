---
description: "Learn more about: Missing or invalid Transaction set identifier"
title: "Missing or invalid Transaction set identifier"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Missing or invalid Transaction set identifier
## Details  
  
| Field | Error Details|
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                     EfactTsMissingOrInvalidTsIdentiferDescription                      |
|  Message Text   |                     Missing or invalid Transaction set identifier                      |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive or send pipeline could not process the EDIFACT interchange because the value of the transaction set identifier (in the UNH2.1 field) was missing or had an invalid value.  
  
## User Action  
 To resolve this error, make sure that the interchange has a value for the UNH2.1 field. Verify that the value of UNH2.1 is a valid one-digit to six-digit document-type designator.
