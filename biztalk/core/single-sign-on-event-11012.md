---
title: "Single Sign-On: Event 11012 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 252bedc8-8dc3-4962-b078-465f9b064ead
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 11012
## Details  
  
|                 |                                                                                                                                                                                                                        |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                               Enterprise Single Sign-On                                                                                                |
| Product Version |                                                                               [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                               |
|    Event ID     |                                                                                                         11012                                                                                                          |
|  Event Source   |                                                                                                         ENTSSO                                                                                                         |
|    Component    |                                                                                                          N/A                                                                                                           |
|  Symbolic Name  |                                                                                           SSO_WARN_NOT_APP_ADMIN_ADMIN_SAME                                                                                            |
|  Message Text   | Client user is not a member of the Application Administrators account.%r<br /><br /> Tracking ID: %1%r<br /><br /> Client User: %2\\%3%r<br /><br /> Application Name: %4%r<br /><br /> Application Administrators: %5 |
  
## Explanation  
 The client user is not a member of the Application Administrators account. This warning only appears when the audit levels are set to high.  
  
## User Action  
 To remedy the situation, you must make the client user a member of the Application Administrators account. To stop this warning from appearing in the future, you can lower the audit levels.