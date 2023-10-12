---
description: "Learn more about: Invalid Version Identifier"
title: "Invalid Version Identifier"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Invalid Version Identifier
## Details  
  
| Field | Error Details |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                       X12Ta1InvalidVersionIdentifierDescription                        |
|  Message Text   |                               Invalid Version Identifier                               |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the version identifier in the interchange (the GS08 field in an X12 interchange or the UNG7 field in an EDIFACT interchange) did not conform to the data type and number of digits established by the service schema (X12ServiceSchema or the EdifactServiceSchema in BaseArtifacts.dll). The GS08 field must be of the X12_AN data type and between 1 and 12 digits. The version in UNG7.1 must be of the EDIFACT_AN data type and between 1 and 3 digits. The release in UNG7.2 must be of the EDIFACT_AN data type and between 1 and 3 digits. The Association assigned code in UNG7.3 must be of the EDIFACT_AN data type and between 1 and 6 digits.  
  
## User Action  
 To resolve this error, make sure that the version in GS08 or UNG7 conforms to the data type and number of digits specified by the service schema, and then have the interchange resent.
