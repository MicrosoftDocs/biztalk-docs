---
title: "Single Sign-On: Event 10741 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 58b6b093-d136-498f-a3b5-c413150da956
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10741
## Details  

|                 |                                                                                           |
|-----------------|-------------------------------------------------------------------------------------------|
|  Product Name   |                                 Enterprise Single Sign-On                                 |
| Product Version |                [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                 |
|    Event ID     |                                           10741                                           |
|  Event Source   |                                          ENTSSO                                           |
|    Component    |                                            N\A                                            |
|  Symbolic Name  |                                SSO_WARN_SAVING_REPLAY_FILE                                |
|  Message Text   | Saving replay or progress file.%r<br /><br /> Saved File: %1%r<br /><br /> Error Code: %2 |

## Explanation  
 This Warning event indicates that SSO is saving a replay or progress file.  

 Replay files are used by password sync when the ENTSSO server cannot contact the SSO database. A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is again lost.  

## User Action  

- No user action is necessary.  

  For more information, see the following resources:  

- [Password Synchronization](../core/password-synchronization2.md)
