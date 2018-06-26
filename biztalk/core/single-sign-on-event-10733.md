---
title: "Single Sign-On: Event 10733 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 01520ae4-f692-4697-82ce-53a8a63b5bd9
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10733
## Details  

|                 |                                                                                                                                                             |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                  Enterprise Single Sign-On                                                                  |
| Product Version |                                                 [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                  |
|    Event ID     |                                                                            10733                                                                            |
|  Event Source   |                                                                           ENTSSO                                                                            |
|    Component    |                                                                             N\A                                                                             |
|  Symbolic Name  |                                                              SSO_WARN_PS_SET_WINDOWS_PASSWORD                                                               |
|  Message Text   | Failed to update the Windows password in the SSO database.%r<br /><br /> Tracking ID: %1%r<br /><br /> Windows Account: %2\\%3%r<br /><br /> Error Code: %4 |

## Explanation  
 This Warning event indicates that Password Sync failed to update the specified Windows account password in the SSO database.  

## User Action  
 To resolve this warning, do one or more of the following:  

- Check the system and application event logs for associated errors.  

- Verify the password for the specified account is a valid Windows password.  

  For more information, see the following resources:  

- [Password Synchronization](../core/password-synchronization2.md)
