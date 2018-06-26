---
title: "Single Sign-On: Event 10519 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e709957e-a690-4a44-a863-07b2a55dae7b
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10519
## Details  

|                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                                                                                                                                         Enterprise Single Sign-On                                                                                                                                                                                                                                          |
| Product Version |                                                                                                                                                                                                                         [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                                                                                                                         |
|    Event ID     |                                                                                                                                                                                                                                                   10519                                                                                                                                                                                                                                                    |
|  Event Source   |                                                                                                                                                                                                                                                   ENTSSO                                                                                                                                                                                                                                                   |
|    Component    |                                                                                                                                                                                                                                                    N\A                                                                                                                                                                                                                                                     |
|  Symbolic Name  |                                                                                                                                                                                                                                        SSO_WARN_BAD_APP_ADMIN_GROUP                                                                                                                                                                                                                                        |
|  Message Text   | The Application Administrators account for this application is not valid. If it is a local account check that this account exists on the server. If it is a domain account contact your domain administrator. Enable the application when the account is valid. You can ignore this message if you are not going to use this application on this computer.%r<br /><br /> Application Name: %1%r<br /><br /> Application Administrators: %2%r<br /><br /> Invalid accounts: %3%r<br /><br /> Error Code: %4 |

## Explanation  
 This Warning event indicates that an Application Administrators group account is not a valid Windows account. There is one Application Administraotrs account group for each affiliate application.  

## User Action  
 To resolve this warning, do one or more of the following:  

- Verify the specified Application Administrators account exists.  

- Use the SSO Administration Utility to verify the specified affiliate application is configured to use the correct application administrators account.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [SSO User Groups](../core/sso-user-groups.md)  

- [SSO Affiliate Applications](../core/sso-affiliate-applications.md)  

- [How to Update the Properties of an Affiliate Application](../core/how-to-update-the-properties-of-an-affiliate-application.md)
