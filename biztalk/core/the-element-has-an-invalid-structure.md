---
description: "Learn more about: The element has an invalid structure"
title: "The element has an invalid structure"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# The element has an invalid structure
## Details  
  
| Field | Error Details |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                      X12NseStructurallyInvalidElementDescription                       |
|  Message Text   |                       The element '{0}' has an invalid structure                       |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange, or the send pipeline could not process the outgoing interchange, because a data element did not have the structure specified by the applicable schema.  
  
## User Action  
 To resolve this error, fix the structure of the data element in the outgoing interchange, or have the sender of the interchange fix the structure of the data element in the incoming interchange, so that it conforms to the document schema.
