---
description: "Learn more about: Data element too short"
title: "Data element too short"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Data element too short
## Details  
  
|       Field     |                           Error Details                                                |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                                           -                                            |
|  Message Text   |                                 Data element too short                                 |
  
## Explanation  
 This Error/Warning/Information event indicates that the EDI receive pipeline or the EDI Send pipeline could not process the incoming interchange because a data element was shorter than the minimum length specified by the schema.  
  
## User Action  
 To resolve this error, lengthen the data element in the interchange that was too short so it is greater than the minimum length. To determine the minimum length, open the schema in the \XSD_Schema folder, search on the data element ID, and identify what the minLength value is.
