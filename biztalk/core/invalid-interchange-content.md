---
description: "Learn more about: Invalid Interchange Content"
title: "Invalid Interchange Content"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Invalid Interchange Content
## Details  
  
| Field | Error Details |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                       X12Ta1InvalidInterchangeContentDescription                       |
|  Message Text   |                              Invalid Interchange Content                               |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange or the send pipeline could not process the outgoing interchange because the data in the interchange did not pass message validation performed by BizTalk Server.  
  
## User Action  
 To resolve this error, identify which part of the interchange failed validation, and which validation it failed. Resolve the issue that caused validation to fail, and then have the interchange resent.
