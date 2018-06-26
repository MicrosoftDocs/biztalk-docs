---
title: "Single Sign-On: Event 10529 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 75ed70e0-8458-4736-883f-a4536f094dc0
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10529
## Details  

|                 |                                                                                                                   |
|-----------------|-------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                             Enterprise Single Sign-On                                             |
| Product Version |                            [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                             |
|    Event ID     |                                                       10529                                                       |
|  Event Source   |                                                      ENTSSO                                                       |
|    Component    |                                                        N\A                                                        |
|  Symbolic Name  |                                            SSO_INFO_GOT_CURRENT_SECRET                                            |
|  Message Text   | Got the current secret from the master secret server.%r<br /><br /> Secret Server Name: %1%r<br /><br /> MSID: %2 |

## Explanation  
 This Information event indicates that SSO has the requested master secret from the master secret server.  

## User Action  

- No user action is necessary.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [How to Generate the Master Secret](../core/how-to-generate-the-master-secret.md)  

- [Managing the Master Secret](../core/managing-the-master-secret.md)
