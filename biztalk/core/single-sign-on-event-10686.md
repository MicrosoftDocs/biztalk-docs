---
title: "Single Sign-On: Event 10686 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a3e71f2a-e51d-4736-b06a-117142d30dae
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10686
## Details  

|                 |                                                                           |
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
