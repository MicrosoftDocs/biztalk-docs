---
description: "Learn more about: Single Sign-On: Event 11031"
title: "Single Sign-On: Event 11031"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 11031
## Details  
  
| Field | Error Details|
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
