---
title: "Single Sign-On: Event 10820 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2da93a2c-d00d-4ca0-a0cf-453cee4bf3c3
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10820
## Details  
  
|                 |                                                                                              |
|-----------------|----------------------------------------------------------------------------------------------|
|  Product Name   |                                  Enterprise Single Sign-On                                   |
| Product Version |                  [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                  |
|    Event ID     |                                            10820                                             |
|  Event Source   |                                            ENTSSO                                            |
|    Component    |                                             N/A                                              |
|  Symbolic Name  |                                ENTSSO_E_REQUIRE_OLD_PASSWORD                                 |
|  Message Text   | When changing the password for an external account the adapter must supply the old password. |
  
## Explanation  
 This application is configured in such a way that the password sync adapter is required to supply the old password.  
  
## User Action  
 Check the configuration of your password sync adapter.