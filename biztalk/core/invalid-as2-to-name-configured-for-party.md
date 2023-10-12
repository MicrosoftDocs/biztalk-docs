---
description: "Learn more about: Invalid AS2-To name configured for Party"
title: "Invalid AS2-To name configured for Party"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Invalid AS2-To name configured for Party
## Details  
  
| Field | Error Details |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       AS2 Engine                                       |
|  Symbolic Name  |                            InvalidAS2ToNameConfiguredError                             |
|  Message Text   |               Invalid AS2-To name configured for Party: {0}   Value: {1}               |
  
## Explanation  
 This Error/Warning/Information event indicates that the AS2 encoder or decoder could not process the AS2 message because the value of the AS2-To header configured for the identified party did not conform to the specifications in AS2 RFC 4130.  
  
## User Action  
 To resolve this error, make sure that the AS2-To header configured for the party conforms to the specifications in section 6.2 of AS2 RFC 4130.
