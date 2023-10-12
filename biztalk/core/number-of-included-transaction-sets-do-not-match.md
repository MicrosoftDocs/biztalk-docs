---
description: "Learn more about: Number of included transaction sets do not match"
title: "Number of included transaction sets do not match"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Number of included transaction sets do not match
## Details  
  
| Field | Error Details|
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                           X12FaNumberOfTsMismatchDescription                           |
|  Message Text   |                    Number of included transaction sets do not match                    |
  
## Explanation  
 This Error/Warning/Information event indicates that the number of transaction sets in the group of the X12 interchange does not equal the number in the group trailer (GE01 field). This occurs when the interchange is preserved and the interchange is suspended on an error. (The error message is not posted if the interchange is preserved and the transaction sets are suspended on an error, or if the interchange is split.)  
  
## User Action  
 To resolve this error, make sure that the number in the GE01 field of the group trailer is the same as the number of transaction sets in the group of the interchange, and then resend the interchange.
