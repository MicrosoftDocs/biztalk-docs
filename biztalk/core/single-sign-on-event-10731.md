---
title: "Single Sign-On: Event 10731 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 605e77f0-61f2-4a97-9ea0-bdc56344e8d9
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10731
## Details  

|                 |                                                                                                                                                                                                                                                                           |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                         Enterprise Single Sign-On                                                                                                                         |
| Product Version |                                                                                                        [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                         |
|    Event ID     |                                                                                                                                   10731                                                                                                                                   |
|  Event Source   |                                                                                                                                  ENTSSO                                                                                                                                   |
|    Component    |                                                                                                                                    N\A                                                                                                                                    |
|  Symbolic Name  |                                                                                                                    SSO_WARN_INVALID_USER_NOT_IN_GROUP                                                                                                                     |
|  Message Text   | A mapping could not be created because the specified user is not a member of the Application Users account.%r<br /><br /> Domain Name: %1%r<br /><br /> User Name: %2%r<br /><br /> Application Name: %3%r<br /><br /> Application Users: %4%r<br /><br /> Error Code: %5 |

## Explanation  
 This Warning event indicates that a mapping could not be created because the specified user is not a member of the Application Users account.  

 An application user's group account exists for each affiliate application. Members of this account can verify their credentials in the affiliate application and can manage their credential mappings in the affiliate application.  

## User Action  
 To resolve this warning, do the following:  

- Add the specified user to the application user's group for the specified affiliate application.  

  For more information, see the following resources:  

- [SSO User Groups](../core/sso-user-groups.md)  

- [SSO Affiliate Applications](../core/sso-affiliate-applications.md)
