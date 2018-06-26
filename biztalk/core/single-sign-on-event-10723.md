---
title: "Single Sign-On: Event 10723 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 00536f3e-26d6-4e19-a98f-e687bb1b6611
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10723
## Details  

|                 |                                                                                                                                                                                                         |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                        Enterprise Single Sign-On                                                                                        |
| Product Version |                                                                       [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                        |
|    Event ID     |                                                                                                  10723                                                                                                  |
|  Event Source   |                                                                                                 ENTSSO                                                                                                  |
|    Component    |                                                                                                   N\A                                                                                                   |
|  Symbolic Name  |                                                                                       SSO_ERROR_REPLAY_SECURITY_1                                                                                       |
|  Message Text   | The security on the replay files directory does not match the security on the replay or progress file.%r<br /><br /> File Name: %1%r<br /><br /> File Security: %2%r<br /><br /> Directory Security: %3 |

## Explanation  
 This Error event indicates that the security on the replay files directory does not match the security on the replay or progress file.  

 Replay files are stored in the replay files directory. By default, the SSO service account is used to create both the replay files and the replay files directory. SSO verifies that no changes have been made to the security configuration of the replay files and replay files directory since they were created. If the replay files directory was created with a different account, this error can be returned when Password Sync attempts to create a replay file in that directory. It is strongly recommended that users not change any security configuration of the replay files and replay files directory.  

## User Action  
 To resolve this error, do the following:  

- Check the account used to create the replay files directory. If the directory is empty, attempt running password sync again. It may be necessary to re-create the directory using the same service account as the SSO service. If you cannot re-create a replay files directory using the same account as the SSO service, check permissions for that account.  

  For more information, see the following resources:  

- [How to Configure Password Synchronization](../core/how-to-configure-password-synchronization.md)  

- [Password Synchronization](../core/password-synchronization2.md)
