---
description: "Learn more about: Single Sign-On: Event 10614"
title: "Single Sign-On: Event 10614"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10614
## Details  
  
| Field | Error Details |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                        Enterprise Single Sign-On                                                                                                        |
| Product Version |                                                                                       [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                        |
|    Event ID     |                                                                                                                  10614                                                                                                                  |
|  Event Source   |                                                                                                                 ENTSSO                                                                                                                  |
|    Component    |                                                                                                                   N/A                                                                                                                   |
|  Symbolic Name  |                                                                                                     SSO_WARN_INVALID_TICKET_TIMEOUT                                                                                                     |
|  Message Text   | The ticket time-out value is not valid for global info update.%r<br /><br /> Ticket time-out: %1 minutes%r<br /><br /> Minimum ticket time-out: 1 minute%r<br /><br /> Maximum ticket time-out: %2 minutes%r<br /><br /> Error Code: %3 |
  
## Explanation  
 The ticket time-out value specified is not valid.  
  
## User Action  
 Use the information supplied in the warning message to fix the value.
