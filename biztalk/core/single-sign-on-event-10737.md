---
title: "Single Sign-On: Event 10737 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2102930b-8b1f-4d48-a14d-e8884dc7f9aa
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10737
## Details  

|                 |                                                                                                                                                                                                                        |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                               Enterprise Single Sign-On                                                                                                |
| Product Version |                                                                               [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                               |
|    Event ID     |                                                                                                         10737                                                                                                          |
|  Event Source   |                                                                                                         ENTSSO                                                                                                         |
|    Component    |                                                                                                          N\A                                                                                                           |
|  Symbolic Name  |                                                                                           SSO_WARN_PS_SET_EXTERNAL_PASSWORD                                                                                            |
|  Message Text   | Failed to update the external password in the SSO database.%r<br /><br /> Tracking ID: %1%r<br /><br /> Adapter: %2%r<br /><br /> Application Name: %3%r<br /><br /> External Account: %4%r<br /><br /> Error Code: %5 |

## Explanation  
 This Warning event indicates that SSO failed to update the external password in the SSO database. There are various possible causes of failure indicated in the warning message; in some cases, this warning might indicate a configuration problem, or the mapping may have been deleted while the password change was in process.  

## User Action  
 To resolve this warning, do the following:  

- Retry the password change.  

- If additional attempts continue to fail, change the password manually using the UI or command line tools.  

  For more information, see the following resources:  

- [Password Synchronization](../core/password-synchronization2.md)
