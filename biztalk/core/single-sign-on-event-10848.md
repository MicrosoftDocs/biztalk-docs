---
description: "Learn more about: Single Sign-On: Event 10848"
title: "Single Sign-On: Event 10848"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10848
## Details  
  
| Field | Error Details |
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
