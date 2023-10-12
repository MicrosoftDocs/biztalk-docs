---
description: "Learn more about: Data element too long"
title: "Data element too long"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Data element too long
## Details  
  
|      Field      |                                Error Details                                           |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                                           -                                            |
|  Message Text   |                                 Data element too long                                  |
  
## Explanation  
 This Error/Warning/Information event indicates that the EDI receive pipeline or the EDI Send pipeline could not process the incoming interchange because a data element was longer than the maximum length specified by the schema.  
  
## User Action  
 To resolve this error, shorten the data element in the interchange that was too long so it is below the maximum limit. To determine the maximum length, open the schema in the \XSD_Schema folder, search on the data element ID, and identify what the maxLength value is.
