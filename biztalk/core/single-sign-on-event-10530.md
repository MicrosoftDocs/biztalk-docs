---
title: "Single Sign-On: Event 10530 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4bb37305-26fe-46a7-958d-3ed7f6876a7b
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10530
## Details  

|                 |                                                                                                                    |
|-----------------|--------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                             Enterprise Single Sign-On                                              |
| Product Version |                             [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                             |
|    Event ID     |                                                       10530                                                        |
|  Event Source   |                                                       ENTSSO                                                       |
|    Component    |                                                        N\A                                                         |
|  Symbolic Name  |                                            SSO_INFO_GOT_PREVIOUS_SECRET                                            |
|  Message Text   | Got the previous secret from the master secret server.%r<br /><br /> Secret Server Name: %1%r<br /><br /> MSID: %2 |

## Explanation  
 This Information event indicates that SSO has the previous master secret.  

## User Action  

- No user action is necessary.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [How to Generate the Master Secret](../core/how-to-generate-the-master-secret.md)  

- [Managing the Master Secret](../core/managing-the-master-secret.md)
