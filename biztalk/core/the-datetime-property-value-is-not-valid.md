---
description: "Learn more about: The datetime property value is not valid"
title: "The datetime property value is not valid"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# The datetime property value is not valid
## Details  
  
| Field | Error Details|
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                                  Err_InvalidDateTime                                   |
|  Message Text   |                       The datetime property value is not valid.                        |
  
## Explanation  
 This Error/Warning/Information event indicates BizTalk Server was unable to compare a context property while trying to decide whether to Batch a message.  
  
## User Action  
 To resolve this error, ensure that the filter provided in Active batches doesn’t specify a context property which has an XSD type of date and the value is invalid date.
