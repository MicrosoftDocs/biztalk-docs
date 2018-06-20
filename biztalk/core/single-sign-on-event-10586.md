---
title: "Single Sign-On: Event 10586 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b7d480e9-dc34-44ac-9272-0caf80237bd9
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10586
## Details  
  
|                 |                                                             |
|-----------------|-------------------------------------------------------------|
|  Product Name   |                  Enterprise Single Sign-On                  |
| Product Version | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]  |
|    Event ID     |                            10586                            |
|  Event Source   |                           ENTSSO                            |
|    Component    |                             N/A                             |
|  Symbolic Name  |                   SSO_WARN_CRED_CACHE_OFF                   |
|  Message Text   | The credential cache has been disabled for this SSO server. |
  
## Explanation  
 The credential cache, which is generally enabled, has been disabled. Only a system administrator can enable or disable the credential cache. Disabling the credential cache will sometimes result in more current credentials from the ENTSSO system, although it could slow down peformance.  
  
## User Action  
 To re-enable the credential cache, see the Afflilate Application Properties table in [SSO Affiliate Applications](../core/sso-affiliate-applications.md).