---
title: "Single Sign-On: Event 11014 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 71e4c9bd-8bda-46ca-9e76-f7b4fa033167
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 11014
## Details  
  
|                 |                                                                                                                                                          |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                Enterprise Single Sign-On                                                                 |
| Product Version |                                                [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                |
|    Event ID     |                                                                          11014                                                                           |
|  Event Source   |                                                                          ENTSSO                                                                          |
|    Component    |                                                                           N/A                                                                            |
|  Symbolic Name  |                                                                  SSO_ERROR_ACCESS_CHECK                                                                  |
|  Message Text   | Access check failed.%r<br /><br /> Client User: %1\\%2%r<br /><br /> Application Name: %3%r<br /><br /> Additional Data: %4%r<br /><br /> Error Code: %5 |
  
## Explanation  
 The access check failed for the client and application listed.  
  
## User Action  
 The additional information should enable you to fix the problem. To avoid this error in the future, you can also lower the audit level.