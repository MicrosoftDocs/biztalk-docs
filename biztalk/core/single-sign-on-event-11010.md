---
title: "Single Sign-On: Event 11010 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 22fcd9f3-83bb-44b0-88fc-197c2ef3e72d
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 11010
## Details  
  
|                 |                                                                                                                                                                                         |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                Enterprise Single Sign-On                                                                                |
| Product Version |                                                               [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                |
|    Event ID     |                                                                                          11010                                                                                          |
|  Event Source   |                                                                                         ENTSSO                                                                                          |
|    Component    |                                                                                           N/A                                                                                           |
|  Symbolic Name  |                                                                               SSO_WARN_NOT_SSO_AFF_ADMIN                                                                                |
|  Message Text   | Client user is not a member of the SSO Affiliate Administrators account.%r<br /><br /> Tracking ID: %1%r<br /><br /> Client User: %2\\%3%r<br /><br /> SSO Affiliate Administrators: %4 |
  
## Explanation  
 The client user is not a member of the SSO Affiliate Administrators account. This warning only appears when the audit levels are set to high.  
  
## User Action  
 To remedy the situation, you must make the client user a member of the SSO Affiliate Administrators account. To stop this warning from appearing in the future, you can lower the audit levels.