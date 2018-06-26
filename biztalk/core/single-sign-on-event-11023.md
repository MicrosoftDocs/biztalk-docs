---
title: "Single Sign-On: Event 11023 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: feeb4ede-6045-46bf-9f2b-65062c583faa
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 11023
## Details  
  
|                 |                                                                                                                                                                                                                                                                                            |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                                 Enterprise Single Sign-On                                                                                                                                  |
| Product Version |                                                                                                                 [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                 |
|    Event ID     |                                                                                                                                           11023                                                                                                                                            |
|  Event Source   |                                                                                                                                           ENTSSO                                                                                                                                           |
|    Component    |                                                                                                                                            N/A                                                                                                                                             |
|  Symbolic Name  |                                                                                                                             SSO_WARN_WINDOWS_PASSWORD_DELETED                                                                                                                              |
|  Message Text   | An invalid Windows password in the SSO database was deleted to prevent account lockout.%r<br /><br /> Use the SSO administration tools to set the external credentials for this Windows account.%r<br /><br /> Tracking ID: %1%r<br /><br /> Adapter: %2%r<br /><br /> Windows Account: %3 |
  
## Explanation  
 An invalid Windows password has been deleted.  
  
## User Action  
 Use the SSO administration tools to set the external credentials for this Windows account. For more information, see [Using SSO](../core/using-sso.md).