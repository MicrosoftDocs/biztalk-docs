---
description: "Learn more about: An empty AS2 message was received and suspended"
title: "An empty AS2 message was received and suspended"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# An empty AS2 message was received and suspended
## Details  
  
|     Field   |         Error Details                                                                          |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       AS2 Engine                                       |
|  Symbolic Name  |                                           -                                            |
|  Message Text   |           An empty AS2 message was received.  The message will be suspended.           |
  
## Explanation  
 This Error/Warning/Information event indicates BizTalk Server could not process the incoming AS2 message because the message does not contain a body. The body must be separated from the headers by two carriage return/line feeds.  
  
## User Action  
 To resolve this error, do the following:  
  
-   Ensure the sending party adds a body (separated from the headers by two carriage return/line feeds) to the AS2 message before sending it.
