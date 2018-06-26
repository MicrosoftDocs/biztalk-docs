---
title: "Single Sign-On: Event 10567 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3f29c8d9-3da2-4de7-b61f-8c586382b68f
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10567
## Details  
  
|                 |                                                                                                                                                                                                           |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                         Enterprise Single Sign-On                                                                                         |
| Product Version |                                                                        [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                         |
|    Event ID     |                                                                                                   10567                                                                                                   |
|  Event Source   |                                                                                                  ENTSSO                                                                                                   |
|    Component    |                                                                                                    N/A                                                                                                    |
|  Symbolic Name  |                                                                                      SSO_WARN_INVALID_APP_USER_GROUP                                                                                      |
|  Message Text   | The Application Users account is not valid for application update.%r<br /><br /> Application Name: %1%r<br /><br /> Application Users: %2%r<br /><br /> Invalid accounts: %3%r<br /><br /> Error Code: %4 |
  
## Explanation  
 You have attempted to update an Application Users account which is either invalid or does not exist.  
  
## User Action  
 Check that the name of the account is correct.