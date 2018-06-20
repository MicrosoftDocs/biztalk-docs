---
title: "Single Sign-On: Event 10693 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 672bac7d-0ccc-4a42-a49d-57e387f4cf3a
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10693
## Details  

|                 |                                                                                                        |
|-----------------|--------------------------------------------------------------------------------------------------------|
|  Product Name   |                                       Enterprise Single Sign-On                                        |
| Product Version |                       [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                       |
|    Event ID     |                                                 10693                                                  |
|  Event Source   |                                                 ENTSSO                                                 |
|    Component    |                                                  N\A                                                   |
|  Symbolic Name  |                                    SSO_WARNING_REPLAY_CANNOT_CREATE                                    |
|  Message Text   | Could not create the replay or progress file.%r<br /><br /> File Name: %1%r<br /><br /> Error Code: %2 |

## Explanation  
 This Warning event indicates that SSO was unable to create a replay and\or progress file when connection to the SSO database was lost.  

 Replay files are used by password sync when the ENTSSO server cannot contact the SSO database. A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is again lost.  

## User Action  
 To resolve this error, do the following:  

- Check System and Application event logs for associated events.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [How to Configure Password Synchronization](../core/how-to-configure-password-synchronization.md)  

- [Password Synchronization](../core/password-synchronization2.md)
