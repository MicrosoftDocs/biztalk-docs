---
description: "Learn more about: Invalid Control Number Value"
title: "Invalid Control Number Value"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Invalid Control Number Value
## Details  
  
| Field | Error Details |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                       X12Ta1InvalidControlNumberValueDescription                       |
|  Message Text   |                              Invalid Control Number Value                              |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the value of a control number (interchange, group, or transaction set) in the interchange did not conform to the data type or did not have the correct number of digits specified by the schema. The schema is the X12ServiceSchema or the EdifactServiceSchema in BaseArtifacts.dll.  
  
## User Action  
 To resolve this error, make sure that the control number conforms to the data type and number of digits specified by the schema, and then have the interchange resent.
