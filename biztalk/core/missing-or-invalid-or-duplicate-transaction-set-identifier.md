---
description: "Learn more about: Missing or invalid or duplicate Transaction set identifier"
title: "Missing or invalid or duplicate Transaction set identifier"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Missing or invalid or duplicate Transaction set identifier
## Details  
  
| Field | Error Details|
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                      X12TsMissingOrInvalidTsIdentiferDescription2                      |
|  Message Text   |            Missing or invalid or duplicate Transaction set identifier '{0}'            |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive or send pipeline could not process the X12 interchange because the value of the transaction set identifier (in the ST01 field) was missing, a duplicate, or had an invalid value. This can occur if the document schema does not have an ST header and an SE trailer.  
  
## User Action  
 To resolve this error, make sure that the interchange has a value for the ST01 field and that the schema has an entry for the ST header and SE trailer. Verify that the value of ST01 is a valid three-digit document-type designator. Verify that the ST01 field is not a duplicate with the ST01 field of another transaction set.
