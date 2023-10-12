---
description: "Learn more about: A BTS MIME error was encountered when attempting to decode an AS2 message"
title: "A BTS MIME error was encountered when attempting to decode an AS2 message"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# A BTS MIME error was encountered when attempting to decode an AS2 message
## Details  
  
|   Parameter     |            Value                                                                                                               |
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
