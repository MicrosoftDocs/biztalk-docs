---
title: "Single Sign-On: Event 10595 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1517478c-7217-4e34-a5cb-ff7deea367ed
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10595
## Details  
  
|                 |                                                                                                                                                                                                                    |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                             Enterprise Single Sign-On                                                                                              |
| Product Version |                                                                             [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                             |
|    Event ID     |                                                                                                       10595                                                                                                        |
|  Event Source   |                                                                                                       ENTSSO                                                                                                       |
|    Component    |                                                                                                        N/A                                                                                                         |
|  Symbolic Name  |                                                                                           SSO_WARN_APP_INCOMPLETE_FIELDS                                                                                           |
|  Message Text   | The application cannot be enabled because the fields are incomplete for this application.%r<br /><br /> Application Name: %1%r<br /><br /> Number of Fields Defined: %2%r<br /><br /> Number of Fields Created: %3 |
  
## Explanation  
 When creating an application at the API level, you specified the number of fields (i.e. UserID, Password) the application would define. Each field that has been defined must also be created. This warning message lists the application name, number of fields defined, and number of fields created.  
  
## User Action  
 Determine which fields were defined but not created, and then go back and create them.