---
title: "Single Sign-On: Event 10575 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6a691812-433c-42ba-a225-873ad1bfee99
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10575
## Details  
  
|                 |                                                                                                                                                                                                   |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                     Enterprise Single Sign-On                                                                                     |
| Product Version |                                                                    [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                     |
|    Event ID     |                                                                                               10575                                                                                               |
|  Event Source   |                                                                                              ENTSSO                                                                                               |
|    Component    |                                                                                                N/A                                                                                                |
|  Symbolic Name  |                                                                                  SSO_INFO_CHANGED_SECRET_SERVER                                                                                   |
|  Message Text   | Updated secret server name.%r<br /><br /> New Secret Server: %1%r<br /><br /> Old Secret Server: %2%r<br /><br /> Tracking ID: %3%r<br /><br /> Client Computer: %4%r<br /><br /> Client User: %5 |
  
## Explanation  
 This is an informational message and can be useful for tracking significant security-related events that occurr within the SSO system. This message states that the secret server name has been updated.  
  
## User Action  
 No user action is required.