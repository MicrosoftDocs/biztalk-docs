---
title: "Single Sign-On: Event 11031 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7ecd24c2-e251-4eb9-b3ca-ec0f095bb23a
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 11031
## Details  
  
|                 |                                                                                                                                                                                                                                                                                         |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                                Enterprise Single Sign-On                                                                                                                                |
| Product Version |                                                                                                               [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                |
|    Event ID     |                                                                                                                                          11031                                                                                                                                          |
|  Event Source   |                                                                                                                                         ENTSSO                                                                                                                                          |
|    Component    |                                                                                                                                           N/A                                                                                                                                           |
|  Symbolic Name  |                                                                                                                         SSO_INFO_PS_WIN_CHANGE_INVALID_MAPPING                                                                                                                          |
|  Message Text   | Windows password change. A mapping for this Windows account has been detected but ignored because it is no longer valid.%r<br /><br /> Tracking ID: %1%r<br /><br /> Windows Account: %2%r<br /><br /> Application: %3%r<br /><br /> External Account: %4%r<br /><br /> Client User: %5 |
  
## Explanation  
 It may be that the Windows account exists and is valid, but is not in the Application Users account.  
  
## User Action  
 Delete the mapping and try to recreate it.