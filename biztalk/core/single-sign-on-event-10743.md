---
title: "Single Sign-On: Event 10743 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a2908bc9-1fac-4ab9-869f-0c5512864da4
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10743
## Details  

|                 |                                                                                                                                                                |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                   Enterprise Single Sign-On                                                                    |
| Product Version |                                                   [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                   |
|    Event ID     |                                                                             10743                                                                              |
|  Event Source   |                                                                             ENTSSO                                                                             |
|    Component    |                                                                              N\A                                                                               |
|  Symbolic Name  |                                                                    SSO_ERROR_REPLAY_STOPPED                                                                    |
|  Message Text   | Replay of stored external password changes stopped due to errors.%r<br /><br /> Replay File: %1%r<br /><br /> Additional Data: %2%r<br /><br /> Error Code: %3 |

## Explanation  
 This Error event indicates that replay of stored external password changes stopped due to errors.  

 Replay files are used by password sync when the ENTSSO server cannot contact the SSO database. A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is again lost.  

## User Action  
 To resolve this error, do the following:  

- Check System and Application event logs for associated events.  

  For more information, see the following resources:  

- [How to Configure Password Synchronization](../core/how-to-configure-password-synchronization.md)  

- [Password Synchronization](../core/password-synchronization2.md)
