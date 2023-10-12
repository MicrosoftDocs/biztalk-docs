---
description: "Learn more about: Error encountered after processing Transaction Set(s) because DocType was not set"
title: "Error encountered after processing Transaction Set(s) because DocType was not set"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Error encountered after processing Transaction Set(s) because DocType was not set
## Details  
  
|     Field       |                         Error Details                                                  |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                                     DocTypeNotSet                                      |
|  Message Text   |     Error encountered after processing {0} Transaction Set(s). DocType was not set     |
  
## Explanation  
 This Error/Warning/Information event indicates that the EDI receive pipeline could not process an incoming transaction set because ST01 (for an X12 interchange) or UNH2.1 (for an EDIFACT interchange) was not set for the transaction set.  
  
## User Action  
 To resolve this error, verify that the ST01 or UNH1 segment for the transaction set in error is set to a valid document type.
