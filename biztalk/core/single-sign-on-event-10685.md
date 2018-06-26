---
title: "Single Sign-On: Event 10685 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 810b37b5-51c4-4201-8d88-0bf7d9e16dae
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10685
## Details  

|                 |                                                                                                      |
|-----------------|------------------------------------------------------------------------------------------------------|
|  Product Name   |                                      Enterprise Single Sign-On                                       |
| Product Version |                      [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                      |
|    Event ID     |                                                10685                                                 |
|  Event Source   |                                                ENTSSO                                                |
|    Component    |                                                 N\A                                                  |
|  Symbolic Name  |                                     SSO_WARN_REPLAY_CANNOT_OPEN                                      |
|  Message Text   | Could not open the replay or progress file.%r<br /><br /> File Name: %1%r<br /><br /> Error Code: %2 |

## Explanation  
 This Warning event indicates that SSO has re-established contact with the SSO database, but was unable to open the replay or progress file. If SSO cannot open a replay file, it will proceed to the next replay file.  

 Replay files are used by password sync when the ENTSSO server cannot contact the SSO database. A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is lost again part-way through playing back of a replay file.  

## User Action  
 To resolve this Warning event, do the following:  

- You should check the System and Application Event logs for associated events to determine why SSO was unable to contact the SSO database.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [How to Configure Password Synchronization](../core/how-to-configure-password-synchronization.md)  

- [Password Synchronization](../core/password-synchronization2.md)
