---
title: "Single Sign-On: Event 10807 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 882c01c6-70db-4986-9f4b-f08335424250
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10807
## Details  
  
|                 |                                                            |
|-----------------|------------------------------------------------------------|
|  Product Name   |                 Enterprise Single Sign-On                  |
| Product Version | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    Event ID     |                           10807                            |
|  Event Source   |                           ENTSSO                           |
|    Component    |                            N/A                             |
|  Symbolic Name  |        ENTSSO_E_TOO_MANY_UNCONFIRMED_NOTIFICATIONS         |
|  Message Text   |            Too many unconfirmed notifications.             |
  
## Explanation  
 Each time a password change notification is sent, a confirmation message is received. In this case, the limit for notifications without confirmation has been exceeded.  
  
## User Action  
 Check the password sync adapter.