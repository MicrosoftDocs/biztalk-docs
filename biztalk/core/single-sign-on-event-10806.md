---
description: "Learn more about: Single Sign-On: Event 10806"
title: "Single Sign-On: Event 10806"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10806
## Details  
  
| Field | Error Details |
|-----------------|-----------------------------------------------------------------------------------|
|  Product Name   |                             Enterprise Single Sign-On                             |
| Product Version |            [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]             |
|    Event ID     |                                       10806                                       |
|  Event Source   |                                      ENTSSO                                       |
|    Component    |                                        N/A                                        |
|  Symbolic Name  |                         ENTSSO_E_APP_ASSIGNED_TO_ADAPTER                          |
|  Message Text   | The application cannot be deleted because it is currently assigned to an adapter. |
  
## Explanation  
 An application cannot be deleted when it is assigned to an adapter.  
  
## User Action  
 Unassign the application from the adapter, and then delete it.
