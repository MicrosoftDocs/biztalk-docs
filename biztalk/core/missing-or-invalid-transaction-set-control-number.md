---
description: "Learn more about: Missing or invalid transaction set control number"
title: "Missing or invalid transaction set control number"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Missing or invalid transaction set control number
## Details  
  
| Field | Error Details|
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                    X12TsMissingOrInvalidTsControlNumberDescription                     |
|  Message Text   |                   Missing or invalid transaction set control number                    |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive or send pipeline could not process the interchange because the value of the transaction set control number (in the ST02 field) was missing or had an invalid value. The transaction set control number must be an alphanumeric value.  
  
## User Action  
 To resolve this error, do one of the following:  
  
1.  Make sure that each transaction set has a transaction set control number.  
  
2.  Make sure that each transaction set control number is an alphanumeric value.
