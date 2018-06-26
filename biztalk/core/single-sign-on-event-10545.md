---
title: "Single Sign-On: Event 10545 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 268cb7be-b191-4335-a4cc-7c15d879507c
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10545
## Details  

|                 |                                                            |
|-----------------|------------------------------------------------------------|
|  Product Name   |                 Enterprise Single Sign-On                  |
| Product Version | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    Event ID     |                           10545                            |
|  Event Source   |                           ENTSSO                           |
|    Component    |                             CO                             |
|  Symbolic Name  |             SSO_WARN_ISSUE_TICKETS_NOT_ALLOWED             |
|  Message Text   |        Tickets are not enabled for the SSO system.         |

## Explanation  
 This Warning event indicates that tickets are not enabled for the SSO System. If ticketing is disabled at the system level, ticketing cannot be used at the Affiliate Application level either. It is possible to enable tickets at the system level and disable it at the Affiliate Application level.  

## User Action  
 To resolve this warning, do the following:  

- Enable tickets at the SSO System level.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [SSO Tickets](../core/sso-tickets.md)  

- [How to Configure the SSO Tickets](../core/how-to-configure-the-sso-tickets.md)
