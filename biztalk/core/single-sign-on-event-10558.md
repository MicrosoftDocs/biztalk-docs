---
description: "Learn more about: Single Sign-On: Event 10558"
title: "Single Sign-On: Event 10558"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10558
## Details  
  
| Field | Error Details |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                  Enterprise Single Sign-On                                                                                   |
| Product Version |                                                                  [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                  |
|    Event ID     |                                                                                            10558                                                                                             |
|  Event Source   |                                                                                            ENTSSO                                                                                            |
|    Component    |                                                                                             N/A                                                                                              |
|  Symbolic Name  |                                                                                  SSO_WARN_USER_OWN_MAPPINGS                                                                                  |
|  Message Text   | Application Users are only allowed to control their own mappings.%r<br /><br /> Domain Name: %1%r<br /><br /> User Name: %2%r<br /><br /> Application Name: %3%r<br /><br /> Client User: %4 |
  
## Explanation  
 An attempt was made by an Application User to control the mappings of a different user. This is not allowed.  
  
## User Action  
 Mappings can only be controlled by the Application Users for those specific mappings.
