---
title: "Single Sign-On: Event 10740 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8e8521e7-32af-4a58-8b1a-66ea1d13f1e1
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10740
## Details  

|                 |                                                                                                                                                            |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                 Enterprise Single Sign-On                                                                  |
| Product Version |                                                 [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                 |
|    Event ID     |                                                                           10740                                                                            |
|  Event Source   |                                                                           ENTSSO                                                                           |
|    Component    |                                                                            N\A                                                                             |
|  Symbolic Name  |                                                               SSO_WARN_INVALID_WINDOWS_USER                                                                |
|  Message Text   | The Windows Account is not valid for application update.%r<br /><br /> Application Name: %1%r<br /><br /> Windows Account: %2%r<br /><br /> Error Code: %3 |

## Explanation  
 This Warning event indicates that the Windows Account (specified in the event message) is not valid for application update. This can occur when changing the Windows account for a Host Group application. Host Group applications are used for single sign-on from external systems to Windows systems. They can map a set of external users to a single Windows account. The Windows account they are mapped to is defined in the Application Users field of the application.  

## User Action  
 To resolve this warning, do the following:  

- Check that the Windows account your are using is valid.  

- Recreate the Windows account with the correct Windows account properties.  

  For more information, see the following resources:  

- [Password Synchronization](../core/password-synchronization2.md)
