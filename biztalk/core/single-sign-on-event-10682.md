---
title: "Single Sign-On: Event 10682 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 46f0f425-3946-4bac-a412-488c4afe460d
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10682
## Details  

|                 |                                                                                                |
|-----------------|------------------------------------------------------------------------------------------------|
|  Product Name   |                                   Enterprise Single Sign-On                                    |
| Product Version |                   [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                   |
|    Event ID     |                                             10682                                              |
|  Event Source   |                                             ENTSSO                                             |
|    Component    |                                              N\A                                               |
|  Symbolic Name  |                               SSO_WARN_REPLAY_INVALID_DIR_FOUND                                |
|  Message Text   | A directory was found in the replay files directory - it will be ignored.%r<br />Directory: %1 |

## Explanation  
 This Warning event indicates that a directory was found in the replay files directory. Replay files are used by password sync when the ENTSSO server cannot contact the SSO database. In this case the password changes are stored in a temporary encrypted file, and are replayed back to the SSO database when it becomes available again. The replay files directory is expected to contain only replay files – this error message is issued if a directory is found.  

## User Action  
 To resolve this warning, do one or more of the following:  

- Use command line tool ssoconfig -replayFiles to  change your replay directory.  

- Delete the bad directory if it is not in use.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [How to Configure Password Synchronization](../core/how-to-configure-password-synchronization.md)  

- [Password Synchronization](../core/password-synchronization2.md)
