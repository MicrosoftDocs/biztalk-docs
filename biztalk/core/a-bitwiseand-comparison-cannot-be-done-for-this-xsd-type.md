---
description: "Learn more about: A BitwiseAnd comparison cannot be done for this XSD type"
title: "A BitwiseAnd comparison cannot be done for this XSD type"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# A BitwiseAnd comparison cannot be done for this XSD type
## Details  
  
|  Parameter  | Value |
|--|--|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                             Err_InvalidBitwiseComparision                              |
|  Message Text   |               A BitwiseAnd comparison cannot be done for this XSD type.                |
  
## Explanation  
 This Error/Warning/Information event indicates BizTalk Server was unable to compare a context property while trying to decide to Batch a message.  
  
## User Action  
 To resolve this error, ensure that the filter provided in Active batches doesn’t specify a context property which has an CSD type that can’t be bitwise compared.
