---
description: "Learn more about: Single Sign-On: Event 10686"
title: "Single Sign-On: Event 10686"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10686
## Details  

| Field | Error Details |
|-----------------|---------------------------------------------------------------------------|
|  Product Name   |                         Enterprise Single Sign-On                         |
| Product Version |        [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]         |
|    Event ID     |                                   10686                                   |
|  Event Source   |                                  ENTSSO                                   |
|    Component    |                                    N\A                                    |
|  Symbolic Name  |                          SSO_INFO_REPLAY_STARTED                          |
|  Message Text   | Replaying stored external password changes.%r<br /><br /> Replay File: %1 |

## Explanation  
 This Information event indicates that SSO is replaying the stored external password changes file. Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.  

## User Action  

- No user action is necessary.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [How to Configure Password Synchronization](../core/how-to-configure-password-synchronization.md)  

- [Password Synchronization](../core/password-synchronization2.md)
