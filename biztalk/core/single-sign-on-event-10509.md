---
title: "Single Sign-On: Event 10509 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f906823f-db3f-45fc-bf61-cbe6a9566bd7
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10509
## Details  

|                 |                                                                |
|-----------------|----------------------------------------------------------------|
|  Product Name   |                   Enterprise Single Sign-On                    |
| Product Version |   [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]   |
|    Event ID     |                             10509                              |
|  Event Source   |                             ENTSSO                             |
|    Component    |                              N\A                               |
|  Symbolic Name  |                 SSO_INFO_SERVICE_REMOVE_FAILED                 |
|  Message Text   | Failed to remove the SSO service.%r<br /><br /> Error Code: %1 |

## Explanation  
 This event indicates that the ENTSSO Service failed to uninstall. This event can only occur during a manual uninstallation of Enterprise Single Sign-On.  

## User Action  
 To resolve this event, do the following:  

- Check both the Application and System event logs for related errors from ENTSSO or other services.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [Installing SSO](../core/installing-sso.md)  

- [Implementing Enterprise Single Sign-On](../core/implementing-enterprise-single-sign-on.md)
