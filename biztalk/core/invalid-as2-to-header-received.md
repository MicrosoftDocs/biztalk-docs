---
description: "Learn more about: Invalid AS2-To header received"
title: "Invalid AS2-To header received"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Invalid AS2-To header received
## Details  
  
| Field | Error Details |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       AS2 Engine                                       |
|  Symbolic Name  |                          InvalidAS2ToNameHeaderReceivedError                           |
|  Message Text   |                      Invalid AS2-To header received.  Value: {0}                       |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the value of the AS2-To header in the message did not conform to the specifications in AS2 RFC 4130.  
  
## User Action  
 To resolve this error, make sure that the value in the AS2-To header of the message conforms to the specifications in section 6.2 of AS2 RFC 4130.
