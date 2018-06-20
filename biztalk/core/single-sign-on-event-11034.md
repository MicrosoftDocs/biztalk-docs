---
title: "Single Sign-On: Event 11034 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 828bc5fb-12ab-4eea-94f2-2434ad0ee033
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 11034
## Details  
  
|                 |                                                                                                                                                                                                                                                                                                                                                                                         |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                                                                                Enterprise Single Sign-On                                                                                                                                                                                |
| Product Version |                                                                                                                                                               [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                                                                |
|    Event ID     |                                                                                                                                                                                          11034                                                                                                                                                                                          |
|  Event Source   |                                                                                                                                                                                         ENTSSO                                                                                                                                                                                          |
|    Component    |                                                                                                                                                                                           N/A                                                                                                                                                                                           |
|  Symbolic Name  |                                                                                                                                                                        SSO_INFO_PS_WIN_CHANGE_APP_INCORRECT_TYPE                                                                                                                                                                        |
|  Message Text   | Windows password change. A mapping for this Windows account has been detected but ignored because the application is not the correct type. Only ‘Individual’ or ‘Group’ type applications support Windows password sync.%r<br /><br /> Tracking ID: %1%r<br /><br /> Windows Account: %2%r<br /><br /> Application: %3%r<br /><br /> External Account: %4%r<br /><br /> Client User: %5 |
  
## Explanation  
 Only ‘Individual’ or ‘Group’ type applications support Windows password sync.  
  
## User Action  
 For more information, see [Password Synchronization](../core/password-synchronization2.md).