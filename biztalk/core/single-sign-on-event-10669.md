---
title: "Single Sign-On: Event 10669 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e88a583d-7385-42dd-841e-aa2d2215dd69
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10669
## Details  

|                 |                                                                                                                                                               |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                   Enterprise Single Sign-On                                                                   |
| Product Version |                                                  [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                   |
|    Event ID     |                                                                             10669                                                                             |
|  Event Source   |                                                                            ENTSSO                                                                             |
|    Component    |                                                                              N\A                                                                              |
|  Symbolic Name  |                                                            SSO_WARN_CHANGE_WINDOWS_PASSWORD_FAILED                                                            |
|  Message Text   | Failed to change the Windows password.%r<br /><br /> Tracking ID: %1%r<br /><br /> Adapter: %2%r<br /><br /> Windows Account: %3%r<br /><br /> Error Code: %4 |

## Explanation  
 This Warning event indicates that SSO failed to change a Windows password. SSO calls the Win32 function NetUserChangePassword function to change the Windows password associated with the mapping. If this function fails this error message is issued. The error code will be the one returned from NetUserChangePassword. See the documentation for this function in MSDN for details. Most likely causes of failure are that the old password was incorrect, or that the new password does not meet the required Windows password policy.  

## User Action  
 To resolve this warning, do one or more of the following:  

- Verify the old password. If the old password is incorrect then it can be set manually in the SSO database using the command line tools or Admin MMC.  

- Verify the new password meets the required Windows password policy. If the password does not meet the Windows password policy then consider using password filters.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [Password Synchronization](../core/password-synchronization2.md)
