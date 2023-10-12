---
description: "Learn more about: Single Sign-On: Event 11057"
title: "Single Sign-On: Event 11057"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 11057
## Details  
  
| Field | Error Details | 
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                Enterprise Single Sign-On                                                                                                                |
| Product Version |                                                                                               [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                |
|    Event ID     |                                                                                                                          11057                                                                                                                          |
|  Event Source   |                                                                                                                         ENTSSO                                                                                                                          |
|    Component    |                                                                                                                           N/A                                                                                                                           |
|  Symbolic Name  |                                                                                                        SSO_WARN_PS_DIRECT_MISSING_INITIAL_CREDS                                                                                                         |
|  Message Text   | Direct password change. Some missing external credential fields for this mapping have been set to default values.%r<br /><br /> Tracking ID: %1%r<br /><br /> Application Name: %2%r<br /><br /> Windows Account: %3%r<br /><br /> External Account: %4 |
  
## Explanation  
 While it is possible to change passwords using Direct Password Sync, this feature only supports one external credential field. In this case the ENTSSO System has encountered more than one external credential field, and has set those fields to default (blank) values.  
  
## User Action  
 No user action is necessary.
