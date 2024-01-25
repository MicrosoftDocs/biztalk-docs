---
description: "Learn more about: Single Sign-On: Event 10595"
title: "Single Sign-On: Event 10595"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10595
## Details  
  
-| Field | Error Details|
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
