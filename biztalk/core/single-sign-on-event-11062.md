---
title: "Single Sign-On: Event 11062 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 55c7c2ea-c671-4853-ac64-8cb80bba98b0
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 11062
## Details  
  
|                 |                                                                                                                                                                                                        |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                       Enterprise Single Sign-On                                                                                        |
| Product Version |                                                                       [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                       |
|    Event ID     |                                                                                                 11062                                                                                                  |
|  Event Source   |                                                                                                 ENTSSO                                                                                                 |
|    Component    |                                                                                                  N/A                                                                                                   |
|  Symbolic Name  |                                                                                    SSO_WARN_PASSWORD_FILTER_FAILED                                                                                     |
|  Message Text   | Password filtering failed. No password filter will be used.%r<br /><br /> Application Name: %1%r<br /><br /> Password Filter String: %2%r<br /><br /> Additional Data: %3%r<br /><br /> Error Code: %4 |
  
## Explanation  
 An error occurred while creating a password filter, and the filter was not created.  
  
## User Action  
 To create the Password Filter using the Create Password Filter Wizard, see [How to Use Password Filters](../core/how-to-use-password-filters.md).