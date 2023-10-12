---
description: "Learn more about: Single Sign-On: Event 11043"
title: "Single Sign-On: Event 11043"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 11043
## Details  
  
| Field | Error Details | 
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                                             Enterprise Single Sign-On                                                                                                                                             |
| Product Version |                                                                                                                            [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                             |
|    Event ID     |                                                                                                                                                       11043                                                                                                                                                       |
|  Event Source   |                                                                                                                                                      ENTSSO                                                                                                                                                       |
|    Component    |                                                                                                                                                        N/A                                                                                                                                                        |
|  Symbolic Name  |                                                                                                                                       SSO_WARN_PS_ADAPTER_REPORTED_FAILURE                                                                                                                                        |
|  Message Text   | The password sync adapter reported a failure while attempting to change the external password. The external password was not updated in the SSO database.%r<br /><br /> Tracking ID: %1%r<br /><br /> Adapter: %2%r<br /><br /> External Account: %3%r<br /><br /> Error Message: %4%r<br /><br /> Error Code: %5 |
  
## Explanation  
 When ENTSSO sends a password change to a password sync adapter, the external password must be successfully changed before ENTSSO makes it in the SSO database. In this case, that did not occur.  
  
## User Action  
 Note the information in the warning message and consult your system administrator.
