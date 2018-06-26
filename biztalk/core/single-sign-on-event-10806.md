---
title: "Single Sign-On: Event 10806 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 23650d6b-b6a4-4c41-96cd-476e5b0f7f63
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10806
## Details  
  
|                 |                                                                                   |
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