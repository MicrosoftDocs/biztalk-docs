---
title: "Single Sign-On: Event 10676 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ec0e86fb-921d-4505-b458-51b565123ea7
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10676
## Details  

|                 |                                                                                                                                                                                                                   |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                             Enterprise Single Sign-On                                                                                             |
| Product Version |                                                                            [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                             |
|    Event ID     |                                                                                                       10676                                                                                                       |
|  Event Source   |                                                                                                      ENTSSO                                                                                                       |
|    Component    |                                                                                                        N\A                                                                                                        |
|  Symbolic Name  |                                                                                          SSO_ERROR_REQUIRE_OLD_PASSWORD                                                                                           |
|  Message Text   | External password change. When changing the password for an external account the adapter must supply the old password.%r<br /><br /> Tracking ID: %1%r<br /><br /> Adapter: %2%r<br /><br /> External Account: %3 |

## Explanation  
 This Error event indicates that the password sync adapter was configured to expect an old password from the external system, but an old password was not provided. Either the external system (the external password sync adapter) is not configured or working as expected or the password sync adapter is incorrectly configured. This error may also return error code symbolic name ENTSSO_E_REQUIRE_OLD_PASSWORD.  

## User Action  
 To resolve this error, do the following:  

-   Use the SSO administration tools to set the user configurable property **Verify Old Password** on the Password Sync Adapter Options properties tab. This property can also be set when creating adapters via the command line tools (ssops.exe) with the flag name `verifyOldPassword` and also when creating a new password sync adapter using the Password Sync Adapter wizard.  

## More info

- [Password Synchronization](../core/password-synchronization2.md)  

- **Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
