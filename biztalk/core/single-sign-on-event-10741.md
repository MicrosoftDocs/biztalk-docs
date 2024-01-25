---
description: "Learn more about: Single Sign-On: Event 10741"
title: "Single Sign-On: Event 10741"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10741
## Details  

| Field | Error Details |
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
