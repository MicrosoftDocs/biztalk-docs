---
description: "Learn more about: Invalid Security Value"
title: "Invalid Security Value"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Invalid Security Value
## Details  
  
| Field | Error Details |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                         X12Ta1InvalidSecurityValueDescription                          |
|  Message Text   |                                 Invalid Security Value                                 |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the Security Information in the ISA04 field or the Recipient Reference Password Value in the UNB6.1 field did not conform to the data type and number of digits established by the service schema (X12ServiceSchema or the EdifactServiceSchema in BaseArtifacts.dll).  
  
## User Action  
 To resolve this error, make sure that the ISA04 field is of the X12_AN data type and is 10 characters long (with or without trailing spaces) or that the UNB6.1 field is of the EDIFACT_AN data type and is between 1 and 14 characters long. Have the interchange resent.
