---
description: "Learn more about: Single Sign-On: Event 10610"
title: "Single Sign-On: Event 10610"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10610
## Details  
  
| Field | Error Details |
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
