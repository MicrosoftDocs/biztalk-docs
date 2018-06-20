---
title: "Single Sign-On: Event 10507 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b02d8dfa-7655-471e-84af-e58d08c3cefd
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10507
## Details  

|                 |                                                                 |
|-----------------|-----------------------------------------------------------------|
|  Product Name   |                    Enterprise Single Sign-On                    |
| Product Version |   [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]    |
|    Event ID     |                              10504                              |
|  Event Source   |                             ENTSSO                              |
|    Component    |                               N\A                               |
|  Symbolic Name  |                 SSO_INFO_SERVICE_INSTALL_FAILED                 |
|  Message Text   | Failed to install the SSO service.%r<br /><br /> Error Code: %1 |

## Explanation  
 This event indicates that the ENTSSO Service failed to install. This event can only occur during a manual installation of Enterprise Single Sign-On.  

## User Action  
 To resolve this event, do the following:  

- Check both the Application and System event logs for related errors from ENTSSO or other services.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [Installing SSO](../core/installing-sso.md)  

- [Implementing Enterprise Single Sign-On](../core/implementing-enterprise-single-sign-on.md)
