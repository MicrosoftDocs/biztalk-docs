---
description: "Learn more about: Single Sign-On: Event 10855"
title: "Single Sign-On: Event 10855"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10855

| Field | Error Details|
|-----------------|------------------------------------------------------------------------|
|  Product Name   |                       Enterprise Single Sign-On                        |
| Product Version |       [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]       |
|    Event ID     |                                 10855                                  |
|  Event Source   |                                 ENTSSO                                 |
|    Component    |                                  N/A                                   |
|  Symbolic Name  |                    ENTSSO_E_PASSWORD_FILTER_FAILED                     |
|  Message Text   | The credentials cannot be returned because the password filter failed. |

## Explanation  
 The password filter is not valid. The most likely cause of this is that the filter was created manually, which is not recommended.  

## User Action  
 Create the password filter again using the Create Filter wizard.
