---
description: "Learn more about: Single Sign-On: Event 10612"
title: "Single Sign-On: Event 10612"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10612
## Details  
  
| Field | Error Details |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                            Enterprise Single Sign-On                                                                                                                            |
| Product Version |                                                                                                           [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                            |
|    Event ID     |                                                                                                                                      10612                                                                                                                                      |
|  Event Source   |                                                                                                                                     ENTSSO                                                                                                                                      |
|    Component    |                                                                                                                                       N/A                                                                                                                                       |
|  Symbolic Name  |                                                                                                                          SSO_WARN_TRANSACTION_TIMEOUT                                                                                                                           |
|  Message Text   | The transaction time-out exceeds the recommended maximum for this operation. See documentation for details.%r<br /><br /> Transaction ID: %1%r<br /><br /> Transaction time-out: %2 minutes (zero indicates an infinite time-out)%r<br /><br /> Recommended maximum: %3 minutes |
  
## Explanation  
 A transaction has entered the system with an exceedingly large timeout value. If the ENTSSO system polls the SSO database while it’s locked by a long-running transaction, the system will eventually go offline.  
  
## User Action  
 No user action is required.
