---
title: "Single Sign-On: Event 10544 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c79e2186-1c75-4e7b-8bf5-f582e5c2aac7
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10544
## Details  

|                 |                                                            |
|-----------------|------------------------------------------------------------|
|  Product Name   |                 Enterprise Single Sign-On                  |
| Product Version | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    Event ID     |                           10544                            |
|  Event Source   |                           ENTSSO                           |
|    Component    |                             CO                             |
|  Symbolic Name  |                  SSO_WARN_TICKET_EXPIRED                   |
|  Message Text   | The ticket has expired.%r<br /><br /> Application Name: %1 |

## Explanation  
 This Warning event indicates that an application ticket timeout has expired. Ticket timeout can be specified at both the system level and the application level. If both system level and the application level timeout are specified, the application level timeout is used to determine the expiry time.  

## User Action  
 To resolve this warning, do one or more of the following:  

- Determine why the ticket expired before being validated.  

- Ensure that the Ticket timeout value is long enough to last between the time when the ticket is issued to the time that it is redeemed.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [SSO Tickets](../core/sso-tickets.md)  

- [How to Configure the SSO Tickets](../core/how-to-configure-the-sso-tickets.md)
