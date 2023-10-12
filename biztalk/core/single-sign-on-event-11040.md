---
description: "Learn more about: Single Sign-On: Event 11040"
title: "Single Sign-On: Event 11040"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 11040
## Details  
  
| Field | Error Details | 
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                  Enterprise Single Sign-On                                                                  |
| Product Version |                                                 [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                  |
|    Event ID     |                                                                            11040                                                                            |
|  Event Source   |                                                                           ENTSSO                                                                            |
|    Component    |                                                                             N/A                                                                             |
|  Symbolic Name  |                                                                  SSO_WARN_NETWORK_SERVICE                                                                   |
|  Message Text   | The SSO service is running under the Network Service account. There are some special considerations for this account. See your documentation for details.%r |
  
## Explanation  
 The SSO service is running under the Network Service account. There are some special considerations for this account. For example, a reboot is required after adding a Network Service account. Also, running under a Network Service account restricts you to running in very limited scenarios.  
  
## User Action  
 For more information, see [SSO Security Recommendations](../core/sso-security-recommendations.md).
