---
title: "Single Sign-On: Event 10818 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6ad54646-4285-42e5-a270-d56935742a95
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10818
## Details  
  
|                 |                                                                                 |
|-----------------|---------------------------------------------------------------------------------|
|  Product Name   |                            Enterprise Single Sign-On                            |
| Product Version |           [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]            |
|    Event ID     |                                      10818                                      |
|  Event Source   |                                     ENTSSO                                      |
|    Component    |                                       N/A                                       |
|  Symbolic Name  |                         ENTSSO_E_AMBIGUOUS_SYNC_FIELDS                          |
|  Message Text   | The application must have two fields or only one field must be marked for sync. |
  
## Explanation  
 If there are more than two fields, then one and only one must be marked for password sync.  
  
## User Action  
 To remedy this situation, you must delete the application and recreate it so that it follows these guidelines.