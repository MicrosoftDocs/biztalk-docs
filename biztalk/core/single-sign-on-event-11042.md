---
title: "Single Sign-On: Event 11042 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c1927bb5-a400-4e3a-8f80-95ef5693216c
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 11042
## Details  
  
|                 |                                                                                                                                                                                                                                                                                                                               |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                                                   Enterprise Single Sign-On                                                                                                                                                   |
| Product Version |                                                                                                                                  [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                                   |
|    Event ID     |                                                                                                                                                             11042                                                                                                                                                             |
|  Event Source   |                                                                                                                                                            ENTSSO                                                                                                                                                             |
|    Component    |                                                                                                                                                              N/A                                                                                                                                                              |
|  Symbolic Name  |                                                                                                                                                SSO_WARN_ACCESS_DENIED_ACCOUNTS                                                                                                                                                |
|  Message Text   | Access denied.<br /><br /> The client user must be a member of one of the following accounts to perform this function.%r<br /><br /> SSO Administrators: %1%r<br /><br /> SSO Affiliate Administrators: %2%r<br /><br /> Application Administrators: %3%r<br /><br /> Application Users: %4%r<br /><br /> Additional Data: %5 |
  
## Explanation  
 The client user must be a member of one of the accounts listed in the warning to perform this function.  
  
## User Action  
 You must join one of the accounts to perform this function.