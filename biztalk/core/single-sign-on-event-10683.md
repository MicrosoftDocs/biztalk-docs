---
title: "Single Sign-On: Event 10683 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 83cd1b96-cd79-4ddc-952b-94a7de216666
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10683
## Details  

|                 |                                                                          |
|-----------------|--------------------------------------------------------------------------|
|  Product Name   |                        Enterprise Single Sign-On                         |
| Product Version |        [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]        |
|    Event ID     |                                  10683                                   |
|  Event Source   |                                  ENTSSO                                  |
|    Component    |                                   N\A                                    |
|  Symbolic Name  |                   SSO_WARN_REPLAY_FILE_DELETED_TOO_OLD                   |
|  Message Text   | A replay file was deleted because it was too old.%r<br />Replay File: %1 |

## Explanation  
 This Warning event indicates that the replay file was deleted because it was too old. Replay files are used by password sync when the ENTSSO server cannot contact the SSO database. In this case the password changes are stored in a temporary encrypted file and are replayed back to the SSO database when it again becomes available. When it is time to replay the files back to the SSO database, if a file is detected that is too old, it is discarded. All old password changes are discarded by the SSO password sync system; the `password sync age` parameter determines the maximum age for password change requests and that can be controlled using the command line tools **ssoconfig –syncAge** or the SSO Admin MMC.  

## User Action  

- No user action is necessary.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [How to Configure Password Synchronization](../core/how-to-configure-password-synchronization.md)  

- [Password Synchronization](../core/password-synchronization2.md)
