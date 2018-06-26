---
title: "Single Sign-On: Event 10539 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a67f5719-da7c-4ae0-a6fe-ff7b653a184d
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10539
## Details  

|                 |                                                            |
|-----------------|------------------------------------------------------------|
|  Product Name   |                 Enterprise Single Sign-On                  |
| Product Version | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    Event ID     |                           10539                            |
|  Event Source   |                           ENTSSO                           |
|    Component    |                             CO                             |
|  Symbolic Name  |              SSO_WARN_SSO_TICKETS_NOT_ALLOWED              |
|  Message Text   |        Tickets are not enabled for the SSO system.         |

## Explanation  
 This Warning event indicates that the use of SSO tickets is not enabled. Allowing the use of SSO tickets is an optional feature of the SSO system. This feature has not been enabled on your SSO system.  

## User Action  
 To resolve this warning, do the following:  

- Contact your SSO Administrator to enable tickets for the SSO system. This can be done using the SSO administration tools (GUI or command line).  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [How to Configure the SSO Tickets](../core/how-to-configure-the-sso-tickets.md)  

- [Using SSO](../core/using-sso.md)
