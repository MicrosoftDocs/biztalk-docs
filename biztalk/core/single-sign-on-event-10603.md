---
description: "Learn more about: Single Sign-On: Event 10603"
title: "Single Sign-On: Event 10603"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10603
## Details  
  
| Field | Error Details |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                             Enterprise Single Sign-On                                                              |
| Product Version |                                             [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                             |
|    Event ID     |                                                                       10603                                                                        |
|  Event Source   |                                                                       ENTSSO                                                                       |
|    Component    |                                                                        N/A                                                                         |
|  Symbolic Name  |                                                                 SSO_WARN_DB_ACCESS                                                                 |
|  Message Text   | Could not access the SSO database. If this condition persists, the SSO service will go offline.%r<br /><br /> %1.%r<br /><br /> SQL Error code: %2 |
  
## Explanation  
 The SSO database is unavailable.  
  
## User Action  
 Check the SQL error code contained in the warning. This may offer some guidance. If not, contact Microsoft Product Support Services.
