---
description: "Learn more about: Single Sign-On: Event 10697"
title: "Single Sign-On: Event 10697"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10697
## Details  

| Field | Error Details |
|-----------------|---------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                           Enterprise Single Sign-On                                           |
| Product Version |                          [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                           |
|    Event ID     |                                                     10697                                                     |
|  Event Source   |                                                    ENTSSO                                                     |
|    Component    |                                                      N\A                                                      |
|  Symbolic Name  |                                       SSO_ERROR_PROGRESS_FILE_MISMATCH                                        |
|  Message Text   | Corruption was detected in the progress file.%r<br /><br /> Replay File: %1%r<br /><br /> Additional Data: %2 |

## Explanation  
 This Error event indicates that SSO has re-established contact with the SSO database, but was unable to open the progress file because of a mismatch with the corresponding replay file. If SSO cannot open a progress file, it will start at the beginning record of the first replay file.  

 Replay files are used by password sync when the ENTSSO server cannot contact the SSO database. A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is again lost.  

## User Action  
 To resolve this error, do the following:  

- Check System and Application event logs for associated events.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [How to Configure Password Synchronization](../core/how-to-configure-password-synchronization.md)  

- [Password Synchronization](../core/password-synchronization2.md)
