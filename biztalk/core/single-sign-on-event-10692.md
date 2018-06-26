---
title: "Single Sign-On: Event 10692 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 78a476ca-32eb-4f37-a807-25850503db6e
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10692
## Details  

|                 |                                                                                                                                                                                                                                                                     |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                      Enterprise Single Sign-On                                                                                                                      |
| Product Version |                                                                                                     [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                      |
|    Event ID     |                                                                                                                                10692                                                                                                                                |
|  Event Source   |                                                                                                                               ENTSSO                                                                                                                                |
|    Component    |                                                                                                                                 N\A                                                                                                                                 |
|  Symbolic Name  |                                                                                                                    SSO_WARN_REPLAY_ACCESS_DENIED                                                                                                                    |
|  Message Text   | The external password change cannot be replayed because the original caller is no longer a member of the access account for the adapter.%r<br /><br /> Replay File: %1%r<br /><br /> Adapter: %2%r<br /><br /> Original Caller: %3%r<br /><br /> Access Account: %4 |

## Explanation  
 This Warning event indicates that SSO has re-established contact with the SSO database, but was unable to make a change (in the SSO database) specified in the replay file because the account that originally specified the change is no longer valid.  

 Replay files are used by password sync when the ENTSSO server cannot contact the SSO database. A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is again lost.  

## User Action  
 To resolve this warning, do the following:  

- Check System and Application event logs for associated events.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [How to Configure Password Synchronization](../core/how-to-configure-password-synchronization.md)  

- [Password Synchronization](../core/password-synchronization2.md)
