---
title: "An End Element was found while looking for Start Element | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f7690744-a795-47cc-bc66-a0314a4cc320
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# An End Element was found while looking for Start Element
## Details  
  
|                 |                                                                                                   |
|-----------------|---------------------------------------------------------------------------------------------------|
|  Product Name   |        [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]         |
| Product Version |                    [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                     |
|    Event ID     |                                                 -                                                 |
|  Event Source   |      [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI       |
|    Component    |                                            EDI Engine                                             |
|  Symbolic Name  |                             EndElementFoundWhenLookingForStartElement                             |
|  Message Text   | An EndElement with name {0} was found, while looking for StartElement with name {1}, at depth {2} |
  
## Explanation  
 This Error/Warning/Information event indicates that BizTalk Server could not process an incoming XML message (after parsing) or an outgoing XML message (before serialization) because the XML message failed validation. The XML message did not contain an end tag for a header or data element.  
  
## User Action  
 To resolve this error, add the appropriate end tag or trailer to the XML message, and then resend the message.