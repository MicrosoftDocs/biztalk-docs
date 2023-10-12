---
description: "Learn more about: Single Sign-On: Event 10585"
title: "Single Sign-On: Event 10585"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10585
## Details  
  
| Field | Error Details|
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                 Enterprise Single Sign-On                                                                                 |
| Product Version |                                                                [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                 |
|    Event ID     |                                                                                           10585                                                                                           |
|  Event Source   |                                                                                          ENTSSO                                                                                           |
|    Component    |                                                                                            N/A                                                                                            |
|  Symbolic Name  |                                                                             SSO_WARN_EXPIRED_TICKET_REDEEMED                                                                              |
|  Message Text   | A ticket is being redeemed after the ticket time-out period has expired. This is allowed because the ticket time-out is disabled for this application.%r<br /><br /> Application Name: %1 |
  
## Explanation  
 Ticket time-out can be enabled or disabled. In this case a ticket is being redeemed even though its time-out period has expired, because the time-out is disabled.  
  
## User Action  
 If the time-out was supposed to be disabled, no user action is required. However, if you were not aware that this particular application had its time-out disabled, check the application immediately to be sure you want to allow it.
