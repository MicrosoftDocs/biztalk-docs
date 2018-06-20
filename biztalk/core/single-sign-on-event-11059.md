---
title: "Single Sign-On: Event 11059 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ac5b6ce7-8819-4b9d-85f7-f5dfaf940487
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 11059
## Details  
  
|                 |                                                                                                                                                                                                                                                       |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                               Enterprise Single Sign-On                                                                                                               |
| Product Version |                                                                                              [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                               |
|    Event ID     |                                                                                                                         11059                                                                                                                         |
|  Event Source   |                                                                                                                        ENTSSO                                                                                                                         |
|    Component    |                                                                                                                          N/A                                                                                                                          |
|  Symbolic Name  |                                                                                                          SSO_INFO_INVALID_USER_NOT_IN_GROUP                                                                                                           |
|  Message Text   | A mapping could not be created because the specified user is not a member of the Application Users account.%r<br /><br /> Windows Account: %1\\%2%r<br /><br /> Application Name: %3%r<br /><br /> Application Users: %4%r<br /><br /> Error Code: %5 |
  
## Explanation  
 The mapping could not be created because the specified user is not a member of the Application Users account.  
  
## User Action  
 Contact your ENTSSO Administrator about becoming a member of the Application Users account.