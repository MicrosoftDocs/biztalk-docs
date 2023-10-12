---
description: "Learn more about: UNA segment is invalid. It did not contain 6 fields"
title: "UNA segment is invalid. It did not contain 6 fields"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# UNA segment is invalid. It did not contain 6 fields
## Details  
  
|      Field      |                                  Error Details                                     |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                             UnaDidNotContainSixDelimiters                              |
|  Message Text   |                  UNA segment is invalid. It did not contain 6 fields                   |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive pipeline could not process the incoming EDIFACT interchange because the UNA segment contained fewer than six data elements.  
  
## User Action  
 To resolve this error, have the sender of the interchange make sure that the UNA segment contains six data elements, and then resend the interchange.
