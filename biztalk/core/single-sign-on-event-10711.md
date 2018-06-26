---
title: "Single Sign-On: Event 10711 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 40722fe1-4be9-40d3-b5c5-a740a4b59f45
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10711
## Details  

|                 |                                                                                                                                                                                                                                                   |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                             Enterprise Single Sign-On                                                                                                             |
| Product Version |                                                                                            [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                             |
|    Event ID     |                                                                                                                       10711                                                                                                                       |
|  Event Source   |                                                                                                                      ENTSSO                                                                                                                       |
|    Component    |                                                                                                                        N\A                                                                                                                        |
|  Symbolic Name  |                                                                                                         SSO_WARN_PS_MISSING_INITIAL_CREDS                                                                                                         |
|  Message Text   | External password change. Some missing external credential fields for this mapping have been set to default values.%r<br /><br /> Tracking ID: %1%r<br /><br /> Adapter: %2%r<br /><br /> Application Name: %3%r<br /><br /> External Account: %4 |

## Explanation  
 This Warning event indicates that an external password change was received with missing credentials. Default values were used in those fields.  

## User Action  
 To resolve this warning, do the following:  

- If necessary, set the credentials to match.  

  For more information, see the following resources:  

- [SSO Affiliate Applications](../core/sso-affiliate-applications.md)  

- [Password Synchronization](../core/password-synchronization2.md)
