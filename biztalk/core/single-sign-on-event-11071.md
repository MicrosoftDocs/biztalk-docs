---
description: "Learn more about: Single Sign-On: Event 11071"
title: "Single Sign-On: Event 11071"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 11071
## Details  
  
| Field | Error Details |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                   Enterprise Single Sign-On                                                                                   |
| Product Version |                                                                  [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                   |
|    Event ID     |                                                                                             11071                                                                                             |
|  Event Source   |                                                                                            ENTSSO                                                                                             |
|    Component    |                                                                                              N/A                                                                                              |
|  Symbolic Name  |                                                                         SSO_WARN_PS_WIN_CHANGE_DISCARDED_ZERO_LENGTH                                                                          |
|  Message Text   | A Windows password change was discarded because the Windows password length is zero characters.%r<br /><br /> Tracking ID: %1%r<br /><br /> Windows Account: %2%r<br /><br /> Client User: %3 |
  
## Explanation  
 A Windows password change was discarded because the Windows password length is zero characters. The Windows account and client user name are provided.  
  
## User Action  
 Change the password again, using the number and type of characters required by your SSO system.
