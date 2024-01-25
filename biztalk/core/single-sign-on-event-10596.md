---
description: "Learn more about: Single Sign-On: Event 10596"
title: "Single Sign-On: Event 10596"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10596
## Details  
  
| Field | Error Details|
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                         Enterprise Single Sign-On                                                                                                          |
| Product Version |                                                                                         [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                         |
|    Event ID     |                                                                                                                   10596                                                                                                                    |
|  Event Source   |                                                                                                                   ENTSSO                                                                                                                   |
|    Component    |                                                                                                                    N/A                                                                                                                     |
|  Symbolic Name  |                                                                                                     SSO_WARN_TICKET_USER_NOT_IN_GROUP                                                                                                      |
|  Message Text   | The ticket cannot be redeemed because the user for whom the ticket was issued is not a member of the Application Users account.%r<br /><br /> Application Name: %1%r<br /><br /> Ticket Issued For: %2%r<br /><br /> Application Users: %3 |
  
## Explanation  
 The ticket cannot be redeemed because the user for whom the ticket was issued is not a member of the Application Users account.  
  
## User Action  
 Reissue the ticket to a user who is a member of the Application Users account.
