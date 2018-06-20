---
title: "An invalid quoted HTTP header encountered | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bb530ee6-ec6a-4791-ae99-b9db426c0896
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# An invalid quoted HTTP header encountered
## Details  
  
|                 |                                                                                                              |
|-----------------|--------------------------------------------------------------------------------------------------------------|
|  Product Name   |              [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]              |
| Product Version |                          [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                          |
|    Event ID     |                                                      -                                                       |
|  Event Source   |            [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI            |
|    Component    |                                                  AS2 Engine                                                  |
|  Symbolic Name  |                                                      -                                                       |
|  Message Text   | An invalid quoted HTTP header encountered.  Details are as follows:  Header Name: "{0}"  Header Value: "{1}" |
  
## Explanation  
 This Error/Warning/Information event indicates that the AS2 receive pipeline or the AS2 send pipeline could not process the AS2 message because the name of the AS2-From or AS2-To HTTP header in the message was not quoted correctly. The header name is quoted in order to accommodate a space, backslash, or double quotes within the name.  
  
## User Action  
 To resolve this error, quote the header name in the AS2 message in accordance with the rules stated in section 6.2, "AS2 System Identifiers", in RFC 4130, "MIME-Based Secure Peer-to-Peer Business Data Interchange Using HTTP, Applicability Statement 2 (AS2)".