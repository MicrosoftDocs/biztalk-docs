---
description: "Learn more about: Too many data elements"
title: "Too many data elements"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Too many data elements
## Details  
  
| Field | Error Details |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                          X12DeTooManyDataElementsDescription                           |
|  Message Text   |                                 Too many data elements                                 |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange or the send pipeline could not process the outgoing interchange because a segment in the interchange contained more data elements than allowed by the document schema or the service schema.  
  
## User Action  
 To resolve this error, have the sender of the interchange ensure that segments include the required number of data elements, removing excess data elements from the segment if necessary, until the segment conforms to the schema.
