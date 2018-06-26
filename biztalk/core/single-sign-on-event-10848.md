---
title: "Single Sign-On: Event 10848 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 61888420-29a6-4c64-a884-1b074b586f21
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10848
## Details  
  
|                 |                                                                                            |
|-----------------|--------------------------------------------------------------------------------------------|
|  Product Name   |                                 Enterprise Single Sign-On                                  |
| Product Version |                 [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                 |
|    Event ID     |                                           10848                                            |
|  Event Source   |                                           ENTSSO                                           |
|    Component    |                                            N/A                                             |
|  Symbolic Name  |                         ENTSSO_E_DIRECT_SYNC_NOT_ALLOWED_AMBIGUOUS                         |
|  Message Text   | Direct password sync is not allowed for this application because its fields are ambiguous. |
  
## Explanation  
 If there are more than two fields, then one and only one must be marked for password sync.  
  
## User Action  
 To remedy this situation, you must delete the application and recreate it so that it follows these guidelines.