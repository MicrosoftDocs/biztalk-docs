---
description: "Learn more about: Single Sign-On: Event 10724"
title: "Single Sign-On: Event 10724"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10724
## Details  

| Field | Error Details |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                     Enterprise Single Sign-On                                                                                      |
| Product Version |                                                                     [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                     |
|    Event ID     |                                                                                               10724                                                                                                |
|  Event Source   |                                                                                               ENTSSO                                                                                               |
|    Component    |                                                                                                N\A                                                                                                 |
|  Symbolic Name  |                                                                                    SSO_ERROR_REPLAY_SECURITY_2                                                                                     |
|  Message Text   | The security on the replay or progress file has been changed from its original value.%r<br /><br /> File Name: %1%r<br /><br /> Current File Security: %2%r<br /><br /> Original File Security: %3 |

## Explanation  
 This Error event indicates that the security on the replay or progress files has been changed.  

 Replay files are stored in the replay files directory. By default, the SSO service account is used to create both the replay files and the replay files directory. SSO verifies that no changes have been made to the security configuration of the replay files and replay files directory since they were created. If the replay files directory was created with a different account, this error can be returned when Password Sync attempts to create a replay file in that directory. It is strongly recommended that users not change any security configuration of the replay files and replay files directory.  

## User Action  
 To resolve this error, do the following:  

- Check permission for the account used to create the replay files. This is typically the SSO system account.  

  For more information, see the following resources:  

- [How to Configure Password Synchronization](../core/how-to-configure-password-synchronization.md)  

- [Password Synchronization](../core/password-synchronization2.md)
