---
title: "Single Sign-On: Event 10849 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fdfb1cea-e445-4318-9891-b6b70a266ca9
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10849
## Details  
  
|                 |                                                                                  |
|-----------------|----------------------------------------------------------------------------------|
|  Product Name   |                            Enterprise Single Sign-On                             |
| Product Version |            [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]            |
|    Event ID     |                                      10849                                       |
|  Event Source   |                                      ENTSSO                                      |
|    Component    |                                       N/A                                        |
|  Symbolic Name  |                     ENTSSO_E_DIRECT_SYNC_NOT_ALLOWED_CREATE                      |
|  Message Text   | An application cannot be created with the ‘direct password sync’ flag specified. |
  
## Explanation  
 An application cannot be created with the ‘direct password sync’ flag specified.  
  
## User Action  
 Create the application without the direct password sync flag. Then add and create the fields, enable the application, and specify the direct password sync flag.