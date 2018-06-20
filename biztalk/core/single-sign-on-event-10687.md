---
title: "Single Sign-On: Event 10687 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 10b3fe2c-a7ba-47e1-a753-4eaa64b01a60
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10687
## Details  

|                 |                                                                                                                       |
|-----------------|-----------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                               Enterprise Single Sign-On                                               |
| Product Version |                              [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                               |
|    Event ID     |                                                         10687                                                         |
|  Event Source   |                                                        ENTSSO                                                         |
|    Component    |                                                          N\A                                                          |
|  Symbolic Name  |                                               SSO_INFO_REPLAY_COMPLETE                                                |
|  Message Text   | Replay of stored external password changes completed.%r<br /><br /> Replay File: %1%r<br /><br /> Additional Data: %2 |

## Explanation  
 This Information event indicates that SSO has completed replaying the stored external password changes file. Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.  

## User Action  

- No user action is necessary.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [How to Configure Password Synchronization](../core/how-to-configure-password-synchronization.md)  

- [Password Synchronization](../core/password-synchronization2.md)
