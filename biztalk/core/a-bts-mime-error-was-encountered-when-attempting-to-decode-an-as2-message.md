---
title: "A BTS MIME error was encountered when attempting to decode an AS2 message | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 65cb5ece-78e4-4b83-b126-4d8c588b2c61
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# A BTS MIME error was encountered when attempting to decode an AS2 message
## Details  
  
|                 |                                                                                                                                    |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                         [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                         |
| Product Version |                                     [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                     |
|    Event ID     |                                                                 -                                                                  |
|  Event Source   |                                                         BizTalk Server EDI                                                         |
|    Component    |                                                             AS2 Engine                                                             |
|  Symbolic Name  |                                                                 -                                                                  |
|  Message Text   | A BTS MIME error was encountered when attempting to decode an AS2 message.  AS2-From: {0}, AS2-To: {1}, MessageId: {2}, Error: {3} |
  
## Explanation  
 This error is encountered when using the BizTalk MIME component to handle part of the MIME processing.  
  
## User Action  
 The full error message provides the information about the problem encountered by the MIME component. Refer to the BTS MIME error information for diagnosis of the problem (this is because the AS2 components use the BizTalk MIME components for part of the MIME processing).