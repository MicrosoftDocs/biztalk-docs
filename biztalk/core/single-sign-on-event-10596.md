---
title: "Single Sign-On: Event 10596 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d70aabcf-aa53-40bf-8937-44f191af1aec
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10596
## Details  
  
|                 |                                                                                                                                                                                                                                            |
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