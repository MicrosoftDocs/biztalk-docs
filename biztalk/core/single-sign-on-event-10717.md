---
title: "Single Sign-On: Event 10717 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 14691e0f-a399-4b4d-9dd5-516bf8d3a167
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10717
## Details  

|                 |                                                                                                                                                  |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                            Enterprise Single Sign-On                                                             |
| Product Version |                                            [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                            |
|    Event ID     |                                                                      10717                                                                       |
|  Event Source   |                                                                      ENTSSO                                                                      |
|    Component    |                                                                       N\A                                                                        |
|  Symbolic Name  |                                                         SSO_ERROR_NEW_REPLAY_DIR_FAILED                                                          |
|  Message Text   | Failed to create the replay files directory.%r<br /><br /> Client User: %1%r<br /><br /> Replay Files Directory: %2%r<br /><br /> Error Code: %3 |

## Explanation  
 This Error event indicates that a replay files directory could not be created.  

 When password changes are received by the SSO service from a password sync adapter, they are stored in the SSO database. If the SSO database is temporarily unavailable, the password changes are stored locally in replay files. Replay files are stored in the replay files directory.  

## User Action  
 To resolve this error, do the following:  

- Check the replay files directory, if one does not exist, attempt to create it manually using the same service account as the SSO service. If you cannot create a replay files directory using the same account as the SSO service, check permissions for that account.  

  For more information, see the following resources:  

- [How to Configure Password Synchronization](../core/how-to-configure-password-synchronization.md)  

- [Password Synchronization](../core/password-synchronization2.md)
