---
title: "Single Sign-On: Event 10610 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f6a400eb-7cf2-49df-befb-caf76e845fdf
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10610
## Details  
  
|                 |                                                                                                                                       |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                       Enterprise Single Sign-On                                                       |
| Product Version |                                      [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                       |
|    Event ID     |                                                                 10610                                                                 |
|  Event Source   |                                                                ENTSSO                                                                 |
|    Component    |                                                                  N/A                                                                  |
|  Symbolic Name  |                                                      SSO_WARN_CRED_CACHE_FAILED                                                       |
|  Message Text   | The credential cache has encountered an unexpected error and has shut down. This may affect performance.%r<br /><br /> Error Code: %1 |
  
## Explanation  
 The credential cache has encountered an unexpected error and has shut down. While this may affect performance, it will not affect functionality.  
  
## User Action  
 Restart the SSO service when convenient.