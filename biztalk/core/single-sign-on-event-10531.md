---
title: "Single Sign-On: Event 10531 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 264941f4-7791-4a1f-a0bf-b992c9ccda64
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10531
## Details  

|                 |                                                                                                                                                                                                  |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                    Enterprise Single Sign-On                                                                                     |
| Product Version |                                                                    [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                    |
|    Event ID     |                                                                                              10531                                                                                               |
|  Event Source   |                                                                                              ENTSSO                                                                                              |
|    Component    |                                                                                               N\A                                                                                                |
|  Symbolic Name  |                                                                                     SSO_ERROR_GET_SECRET_OK                                                                                      |
|  Message Text   | A request to get a master secret succeeded.%r<br /><br /> Secret Number: %1%r<br /><br /> MSID: %2%r<br /><br /> Client User: %3%r<br /><br /> Client Computer: %4%r<br /><br /> Tracking ID: %5 |

## Explanation  
 This event indicates that a request for master secret has succeeded.  

## User Action  

- No user action is necessary.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [How to Generate the Master Secret](../core/how-to-generate-the-master-secret.md)  

- [Managing the Master Secret](../core/managing-the-master-secret.md)
