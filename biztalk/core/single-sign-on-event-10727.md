---
title: "Single Sign-On: Event 10727 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8ff7ac94-6f1e-4e56-853e-efc50b1fa1b6
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10727
## Details  

|                 |                                                                                                                                          |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                        Enterprise Single Sign-On                                                         |
| Product Version |                                        [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                        |
|    Event ID     |                                                                  10727                                                                   |
|  Event Source   |                                                                  ENTSSO                                                                  |
|    Component    |                                                                   N\A                                                                    |
|  Symbolic Name  |                                                      SSO_WARN_REPLAY_RECORD_FAILED                                                       |
|  Message Text   | Replay of the stored external password change failed.%r<br /><br /> Adapter: %1%r<br /><br /> File Name: %2%r<br /><br /> Error Code: %3 |

## Explanation  
 This Warning indicates that SSO was unable to replay a password change recorded in the replay file.  

 Replay files are used by password sync when the ENTSSO server cannot contact the SSO database. A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is again lost.  

## User Action  
 To resolve this warning, do the following:  

- Check System and Application event logs for associated events.  

  For more information, see the following resources:  

- [How to Configure Password Synchronization](../core/how-to-configure-password-synchronization.md)  

- [Password Synchronization](../core/password-synchronization2.md)
