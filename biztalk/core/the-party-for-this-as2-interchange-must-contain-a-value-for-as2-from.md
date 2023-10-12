---
description: "Learn more about: The party for this AS2 interchange must contain a value for AS2-From"
title: "The party for this AS2 interchange must contain a value for AS2-From"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# The party for this AS2 interchange must contain a value for AS2-From
## Details  
  
| Field | Error Details |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       AS2 Engine                                       |
|  Symbolic Name  |                              InvalidAgreementAS2FromName                               |
|  Message Text   |         The party for this AS2 interchange must contain a value for AS2-From.          |
  
## Explanation  
 This Error/Warning/Information event indicates that the send pipeline could not send the AS2 message because the AS2-From property was not set for the resolved party as message receiver.  
  
## User Action  
 To resolve this error, open the BizTalk Server Administration Console, move to the Parties node, open the AS2 Properties dialog box for the party resolved for the message, click the Party as AS2 Message Receiver node, and then enter a value for the AS2-From property.
