---
description: "Learn more about: Number of included groups do not match"
title: "Number of included groups do not match"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Number of included groups do not match
## Details  
  
| Field | Error Details|
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                     X12Ta1InvalidNumberOfIncludedGroupsDescription                     |
|  Message Text   |                         Number Of included groups do not match                         |
  
## Explanation  
 This Error/Warning/Information event indicates that the number of groups in the interchange does not equal the number in the interchange trailer (IEA01 field). This occurs when the interchange is preserved and the interchange is suspended on an error. (The error message is not posted if the interchange is preserved and the transaction sets are suspended on an error, or if the interchange is split.)  
  
## User Action  
 To resolve this error, make sure that the number in the IEA01 field of the interchange trailer is the same as the number of groups in the interchange, and then resend the interchange.
