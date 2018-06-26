---
title: "Single Sign-On: Event 10560 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8677a807-2973-4753-8816-c93c45697d92
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10560
## Details  
  
|                 |                                                                                                                                                                                             |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                  Enterprise Single Sign-On                                                                                  |
| Product Version |                                                                 [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                  |
|    Event ID     |                                                                                            10560                                                                                            |
|  Event Source   |                                                                                           ENTSSO                                                                                            |
|    Component    |                                                                                             N/A                                                                                             |
|  Symbolic Name  |                                                                               SSO_ERROR_BACKUP_SECRET_FAILED                                                                                |
|  Message Text   | Failed to back up the master secrets.%r<br /><br /> File Name: %1%r<br /><br /> Current MSID: %2%r<br /><br /> Previous MSID: %3%r<br /><br /> Client User: %4%r<br /><br /> Error Code: %5 |
  
## Explanation  
 An attempt to back up the master secret has failed. The user attempting this backup may have had the wrong permissions, path, or directory.  
  
## User Action  
 For information on backing up the master secret, see [Managing the Master Secret](../core/managing-the-master-secret.md).