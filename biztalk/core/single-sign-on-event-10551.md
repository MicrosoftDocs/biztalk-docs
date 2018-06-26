---
title: "Single Sign-On: Event 10551 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 33434989-08d8-4d13-a3cc-4c5543add69c
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10551
## Details  
  
|                 |                                                                                                                                                                                                                               |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                   Enterprise Single Sign-On                                                                                                   |
| Product Version |                                                                                  [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                   |
|    Event ID     |                                                                                                             10551                                                                                                             |
|  Event Source   |                                                                                                            ENTSSO                                                                                                             |
|    Component    |                                                                                                              N/A                                                                                                              |
|  Symbolic Name  |                                                                                                     SSO_WARN_INVALID_USER                                                                                                     |
|  Message Text   | A mapping could not be created because the specified user is not valid for this application.%r<br /><br /> Domain Name: %1%r<br /><br /> User Name: %2%r<br /><br /> Application Name: %3%r<br /><br /> Application Users: %4 |
  
## Explanation  
 The specified user is not valid. This could be a typing error.  
  
## User Action  
 Check the User Name listed in the warning information, confirm that it is correct, and then create the mapping again.