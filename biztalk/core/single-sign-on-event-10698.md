---
description: "Learn more about: Single Sign-On: Event 10698"
title: "Single Sign-On: Event 10698"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10698
## Details  

| Field | Error Details |
|-----------------|----------------------------------------------------------------------|
|  Product Name   |                      Enterprise Single Sign-On                       |
| Product Version |      [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]      |
|    Event ID     |                                10698                                 |
|  Event Source   |                                ENTSSO                                |
|    Component    |                                 N\A                                  |
|  Symbolic Name  |                     SSO_INFO_REPLAY_FILE_DELETED                     |
|  Message Text   | The replay or progress file was deleted.%r<br /><br /> File Name: %1 |

## Explanation  
 This Information event indicates that SSO has deleted a replay and\or progress file.  

 Replay files are used by password sync when the ENTSSO server cannot contact the SSO database. A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is again lost.  

## User Action  

- No user action is necessary.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [How to Configure Password Synchronization](../core/how-to-configure-password-synchronization.md)  

- [Password Synchronization](../core/password-synchronization2.md)
