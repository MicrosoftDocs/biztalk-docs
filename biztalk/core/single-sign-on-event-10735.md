---
description: "Learn more about: Single Sign-On: Event 10735"
title: "Single Sign-On: Event 10735"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10735
## Details  

| Field | Error Details |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                             Enterprise Single Sign-On                                                                                                              |
| Product Version |                                                                                             [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                             |
|    Event ID     |                                                                                                                       10735                                                                                                                        |
|  Event Source   |                                                                                                                       ENTSSO                                                                                                                       |
|    Component    |                                                                                                                        N\A                                                                                                                         |
|  Symbolic Name  |                                                                                                              SSO_WARN_PS_APP_DISABLED                                                                                                              |
|  Message Text   | External password change. The password was not changed for the external account because the application is disabled.%r<br /><br /> Tracking ID: %1%r<br /><br /> Adapter: %2%r<br /><br /> Application Name: %3%r<br /><br /> External Account: %4 |

## Explanation  
 This Warning event indicates that a password was not changed for the external account because the application is disabled.  

## User Action  
 To resolve this warning, do the following:  

- Enable the affiliate application  

  For more information, see the following resources:  

- [How to Enable an Affiliate Application](../core/how-to-enable-an-affiliate-application.md)  

- [Password Synchronization](../core/password-synchronization2.md)
