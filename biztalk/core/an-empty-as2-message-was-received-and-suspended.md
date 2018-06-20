---
title: "An empty AS2 message was received and suspended | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 349f7134-d039-44ab-b2b3-d378d38dfd38
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# An empty AS2 message was received and suspended
## Details  
  
|                 |                                                                                        |
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