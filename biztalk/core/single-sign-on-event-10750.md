---
title: "Single Sign-On: Event 10750 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2a0fdaf2-d429-40b9-adc3-eb134687fb1a
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10750
## Details  

|                 |                                                                                                                                                                                                                                                                  |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                    Enterprise Single Sign-On                                                                                                                     |
| Product Version |                                                                                                    [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                    |
|    Event ID     |                                                                                                                              10750                                                                                                                               |
|  Event Source   |                                                                                                                              ENTSSO                                                                                                                              |
|    Component    |                                                                                                                               N\A                                                                                                                                |
|  Symbolic Name  |                                                                                                                SSO_ERROR_PS_WRONG_USER_NAME_TYPE                                                                                                                 |
|  Message Text   | PasswordChangeNotify: Incorrect User Name Type. The only accepted value is USER_NAME_TYPE_NT4.<br /><br /> The target is incorrectly configured in Active Directory.%r<br /><br /> User Name Type: %1%r<br /><br /> Client User: %2%r<br /><br /> Error Code: %3 |

## Explanation  
 This Error event indicates that Password Sync received a password change from the Password Change Notification Service (PCNS), but the password change was in the wrong format.  

## User Action  
 To resolve this error, do the following:  

- Check the PCNS configuration. PCNS can run only on a domain controller.  

- Configure User Name Type to USER_NAME_TYPE_NT4 in Active Directory.  

  For more information, see the following resources:  

- Refer to Active Directory documentation for information on how to specify User Name Type.  

- [Password Synchronization](../core/password-synchronization2.md)
