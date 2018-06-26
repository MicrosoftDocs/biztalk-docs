---
title: "Single Sign-On: Event 10599 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cd671aa5-b243-4081-9a4e-87103be9a1d7
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10599
## Details  
  
|                 |                                                                                                                                                                                    |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                             Enterprise Single Sign-On                                                                              |
| Product Version |                                                             [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                             |
|    Event ID     |                                                                                       10599                                                                                        |
|  Event Source   |                                                                                       ENTSSO                                                                                       |
|    Component    |                                                                                        N/A                                                                                         |
|  Symbolic Name  |                                                                              SSO_WARN_ENTSSO_IS_ADMIN                                                                              |
|  Message Text   | The SSO service is running under a local administrator account. This is not recommended for security reasons. See documentation for details.%r<br /><br /> SSO Service Account: %1 |
  
## Explanation  
 The SSO service specified is running under a local administrator account. This is not recommended for security reasons.  
  
## User Action  
 For more information, see [SSO Security Recommendations](../core/sso-security-recommendations.md).