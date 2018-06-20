---
title: "Single Sign-On: Event 10549 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1a18eb63-700c-4f49-acc4-890abe2a00ff
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10549
## Details  

|                 |                                                                                                                                                                                          |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                Enterprise Single Sign-On                                                                                 |
| Product Version |                                                                [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                |
|    Event ID     |                                                                                          10549                                                                                           |
|  Event Source   |                                                                                          ENTSSO                                                                                          |
|    Component    |                                                                                            CO                                                                                            |
|  Symbolic Name  |                                                                             SSO_ERROR_CREATE_DATABASE_FAILED                                                                             |
|  Message Text   | Creation and initialization of the SSO database failed.%r<br /><br /> SQL Server Name: %1%r<br /><br /> SSO Database Name: %2%r<br /><br /> Client User: %3%r<br /><br /> Error Code: %4 |

## Explanation  
 This Error indicates that creation and initialization of the SSO database failed.  

## User Action  
 To resolve this error do the following:  

- Check the system and application event logs for associated messages.  

- Run Setup again.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [Installing SSO](../core/installing-sso.md)
