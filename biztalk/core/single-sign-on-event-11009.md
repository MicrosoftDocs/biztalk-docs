---
description: "Learn more about: Single Sign-On: Event 11009"
title: "Single Sign-On: Event 11009"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 11009
## Details  
  
| Field | Error Details|
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                      Enterprise Single Sign-On                                                                      |
| Product Version |                                                     [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                      |
|    Event ID     |                                                                                11009                                                                                |
|  Event Source   |                                                                               ENTSSO                                                                                |
|    Component    |                                                                                 N/A                                                                                 |
|  Symbolic Name  |                                                                       SSO_WARN_NOT_SSO_ADMIN                                                                        |
|  Message Text   | Client user is not a member of the SSO Administrators account.%r<br /><br /> Tracking ID: %1%r<br /><br /> Client User: %2\\%3%r<br /><br /> SSO Administrators: %4 |
  
## Explanation  
 The client user is not a member of the SSO Administrators account. This warning only appears when the audit levels are set to high.  
  
## User Action  
 To remedy the situation, you must make the client user a member of the SSO Administrators account. To stop this warning from appearing in the future, you can lower the audit levels.
