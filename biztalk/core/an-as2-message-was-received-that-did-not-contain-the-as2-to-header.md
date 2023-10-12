---
description: "Learn more about: An AS2 message was received that did not contain the AS2-To header"
title: "An AS2 message was received that did not contain the AS2-To header"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# An AS2 message was received that did not contain the AS2-To header
## Details  
  
|   Field     |        Error Details                                                                           |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       AS2 Engine                                       |
|  Symbolic Name  |                                           -                                            |
|  Message Text   |           An AS2 message was received that did not contain the AS2-To header           |
  
## Explanation  
 This Error/Warning/Information event indicates BizTalk Server could not process the incoming AS2 message because the message did not contain an AS2-To header indicating the source of the message. An AS2 message must have an AS2-To header. The message will be suspended if it does not have an AS2-To header.  
  
## User Action  
 To resolve this error, do the following:  
  
-   Ensure the sending party adds an AS2-To header to the HTTP, AS2, and MIME header of the AS2 message before sending it.
