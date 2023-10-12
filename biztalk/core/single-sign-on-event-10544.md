---
description: "Learn more about: Single Sign-On: Event 10544"
title: "Single Sign-On: Event 10544"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10544
## Details  

| Field | Error Details |
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
