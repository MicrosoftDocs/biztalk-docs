---
title: "The party for this AS2 interchange must contain a value for AS2-To | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 029eae5d-4c13-402d-90c5-8e9ef3814a1f
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# The party for this AS2 interchange must contain a value for AS2-To
## Details  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       AS2 Engine                                       |
|  Symbolic Name  |                               InvalidAgreementAS2ToName                                |
|  Message Text   |          The party for this AS2 interchange must contain a value for AS2-To.           |
  
## Explanation  
 This Error/Warning/Information event indicates that the send pipeline could not process the outgoing AS2 message because the AS2-To property was not set for the resolved party as message receiver. This indicates that the party for the outgoing AS2 message was resolved by matching the send port associated with the party with the send port that subscribed to the message.  
  
## User Action  
 To resolve this error, do as follows:  
  
1.  Open the BizTalk Server Administration Console.  
  
2.  Move to the Parties node, and open the AS2 Properties dialog box for the party resolved for the message.  
  
3.  Click the Party as AS2 Message Receiver node.  
  
4.  Enter a value for the AS2-To property.