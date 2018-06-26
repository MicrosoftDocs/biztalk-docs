---
title: "Single Sign-On: Event 11035 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d551083c-a897-4a76-a40c-2254d3a3e52e
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 11035
## Details  
  
|                 |                                                                                                                                                                                                                                                                                                                        |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                                               Enterprise Single Sign-On                                                                                                                                                |
| Product Version |                                                                                                                               [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                               |
|    Event ID     |                                                                                                                                                         11035                                                                                                                                                          |
|  Event Source   |                                                                                                                                                         ENTSSO                                                                                                                                                         |
|    Component    |                                                                                                                                                          N/A                                                                                                                                                           |
|  Symbolic Name  |                                                                                                                                           SSO_INFO_PS_WIN_CHANGE_NO_ADAPTER                                                                                                                                            |
|  Message Text   | Windows password change. A mapping for this Windows account has been detected but ignored because password sync is not configured for this application.%r<br /><br /> Tracking ID: %1%r<br /><br /> Windows Account: %2%r<br /><br /> Application: %3%r<br /><br /> External Account: %4%r<br /><br /> Client User: %5 |
  
## Explanation  
 A mapping for this Windows account has been detected but ignored because password sync is not configured for this application.  
  
## User Action  
 For information on configuring Password Sync, see [Password Synchronization](../core/password-synchronization2.md).