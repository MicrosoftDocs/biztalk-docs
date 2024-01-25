---
description: "Learn more about: Single Sign-On: Event 10818"
title: "Single Sign-On: Event 10818"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10818
## Details  
  
| Field | Error Details |
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
