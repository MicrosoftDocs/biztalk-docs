---
description: "Learn more about: Invalid AS2-From name encountered during processing"
title: "Invalid AS2-From name encountered during processing"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Invalid AS2-From name encountered during processing
## Details  
  
| Field | Error Details |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       AS2 Engine                                       |
|  Symbolic Name  |                           InvalidAS2FromNameEncounteredError                           |
|  Message Text   |            Invalid AS2-From name encountered during processing.  Value: {0}            |
  
## Explanation  
 This Error/Warning/Information event indicates that either the receive pipeline could not process the incoming interchange or the send pipeline could not process the outgoing interchange because the value of the AS2-From header did not conform to the specifications in AS2 RFC 4130.  
  
## User Action  
 To resolve this error, make sure that the AS2-From header in the incoming or outgoing message conforms to the specifications in section 6.2 of AS2 RFC 4130, and then have the message resent.
