---
description: "Learn more about: Single Sign-On: Event 11036"
title: "Single Sign-On: Event 11036"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 11036
## Details  
  
| Field | Error Details | 
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
