---
title: "Single Sign-On: Event 11036 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2dad0427-83dd-42ac-b0bc-d113abdc8e89
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 11036
## Details  
  
|                 |                                                                                                                                                                                                                                                                                                                                                         |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                                                                Enterprise Single Sign-On                                                                                                                                                                |
| Product Version |                                                                                                                                               [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                                                |
|    Event ID     |                                                                                                                                                                          11036                                                                                                                                                                          |
|  Event Source   |                                                                                                                                                                         ENTSSO                                                                                                                                                                          |
|    Component    |                                                                                                                                                                           N/A                                                                                                                                                                           |
|  Symbolic Name  |                                                                                                                                                         SSO_INFO_PS_WIN_CHANGE_ADAPTER_NO_SYNC                                                                                                                                                          |
|  Message Text   | Windows password change. A mapping for this Windows account has been detected but ignored because the adapter configured for this application does not support password sync to external systems.%r<br /><br /> Tracking ID: %1%r<br /><br /> Windows Account: %2%r<br /><br /> Application: %3%r<br /><br /> Adapter: %4%r<br /><br /> Client User: %5 |
  
## Explanation  
 A mapping for this Windows account has been detected but ignored because the adapter configured for this application does not support password sync to external systems.  
  
## User Action  
 Check your adapter configuration.  
  
 For information on Password Sync, see [Password Synchronization](../core/password-synchronization2.md).