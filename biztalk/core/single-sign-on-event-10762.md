---
description: "Learn more about: Single Sign-On: Event 10762"
title: "Single Sign-On: Event 10762"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10762
## Details  
  
| Field | Error Details |
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
