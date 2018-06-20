---
title: "Single Sign-On: Event 10568 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 266fd09a-c7e6-4a69-ac1c-1834097fa393
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10568
## Details  
  
|                 |                                                                                                                                                                                                                             |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                  Enterprise Single Sign-On                                                                                                  |
| Product Version |                                                                                 [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                  |
|    Event ID     |                                                                                                            10568                                                                                                            |
|  Event Source   |                                                                                                           ENTSSO                                                                                                            |
|    Component    |                                                                                                             N/A                                                                                                             |
|  Symbolic Name  |                                                                                              SSO_WARN_INVALID_APP_ADMIN_GROUP                                                                                               |
|  Message Text   | The Application Administrators account is not valid for application update.%r<br /><br /> Application Name: %1%r<br /><br /> Application Administrators: %2%r<br /><br /> Invalid accounts: %3%r<br /><br /> Error Code: %4 |
  
## Explanation  
 You have attempted to update an Application Administrators account which is either invalid or does not exist.  
  
## User Action  
 Check that the name of the account is correct.