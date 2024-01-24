---
description: "Learn more about: Single Sign-On: Event 10820"
title: "Single Sign-On: Event 10820"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10820
## Details  
  
| Field | Error Details |
|-----------------|----------------------------------------------------------------------------------------------|
|  Product Name   |                                  Enterprise Single Sign-On                                   |
| Product Version |                  [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                  |
|    Event ID     |                                            10820                                             |
|  Event Source   |                                            ENTSSO                                            |
|    Component    |                                             N/A                                              |
|  Symbolic Name  |                                ENTSSO_E_REQUIRE_OLD_PASSWORD                                 |
|  Message Text   | When changing the password for an external account the adapter must supply the old password. |
  
## Explanation  
 This application is configured in such a way that the password sync adapter is required to supply the old password.  
  
## User Action  
 Check the configuration of your password sync adapter.
