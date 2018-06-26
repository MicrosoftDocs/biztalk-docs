---
title: "Single Sign-On: Event 10710 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 469dc407-be7a-45a1-bcf5-2ba7060a19e2
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10710
## Details  

|                 |                                                                                                                                                                             |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                          Enterprise Single Sign-On                                                                          |
| Product Version |                                                         [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                          |
|    Event ID     |                                                                                    10710                                                                                    |
|  Event Source   |                                                                                   ENTSSO                                                                                    |
|    Component    |                                                                                     N\A                                                                                     |
|  Symbolic Name  |                                                                        SSO_INFO_PS_WIN_CHANGE_DAMPED                                                                        |
|  Message Text   | A Windows password change was damped (detected as a duplicate and discarded).%r<br /><br /> Tracking ID: %1%r<br /><br /> Windows Account: %2%r<br /><br /> Client User: %3 |

## Explanation  
 This Information event indicates that a Windows password change was discarded because it was detected as a duplicate.  

## User Action  

- No user action is necessary.  

  For more information, see the following resources:  

- [Password Synchronization](../core/password-synchronization2.md)
