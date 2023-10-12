---
description: "Learn more about: Single Sign-On: Event 10851"
title: "Single Sign-On: Event 10851"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10851
## Details  
  
| Field | Error Details |
|-----------------|-------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                             Enterprise Single Sign-On                                             |
| Product Version |                            [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                             |
|    Event ID     |                                                       10851                                                       |
|  Event Source   |                                                      ENTSSO                                                       |
|    Component    |                                                        N/A                                                        |
|  Symbolic Name  |                                     ENTSSO_E_PSADMIN_NO_DIRECT_PASSWORD_SYNC                                      |
|  Message Text   | The application cannot be assigned to a password sync adapter because it has the 'direct password sync' flag set. |
  
## Explanation  
 An application cannot use both direct password sync and a password sync adapter.  
  
## User Action  
 Review your application and decide whether or not it should have direct password sync. If it should, leave the flag set as it is and do not attempt to assign the application to a password sync adapter. If it should not, then turn the flag off and assign the application to a password sync adapter as appropriate.
