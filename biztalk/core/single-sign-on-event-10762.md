---
title: "Single Sign-On: Event 10762 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 516e120d-e72b-4f40-9a81-9131ea247dd0
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10762
## Details  
  
|                 |                                                                                                                                |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                   Enterprise Single Sign-On                                                    |
| Product Version |                                   [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                   |
|    Event ID     |                                                             10762                                                              |
|  Event Source   |                                                             ENTSSO                                                             |
|    Component    |                                                              N/A                                                               |
|  Symbolic Name  |                                                     ENTSSO_E_WRONG_THREAD                                                      |
|  Message Text   | The SSO client component has been called on the wrong thread. It is currently locked to a thread because it has a transaction. |
  
## Explanation  
 Components can only be multi-threaded when they do not have a transaction. This component has a transaction so it is locked to a thread.  
  
## User Action  
 Configure your application so that it will not call SSO client components on multiple threads when using transactions.