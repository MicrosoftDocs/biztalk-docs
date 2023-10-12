---
description: "Learn more about: Single Sign-On: Event 10705"
title: "Single Sign-On: Event 10705"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10705
## Details  

| Field | Error Details |
|-----------------|------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                         Enterprise Single Sign-On                                          |
| Product Version |                         [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                         |
|    Event ID     |                                                   10705                                                    |
|  Event Source   |                                                   ENTSSO                                                   |
|    Component    |                                                    N\A                                                     |
|  Symbolic Name  |                                          SSO_WARN_PS_NOT_ADAPTER                                           |
|  Message Text   | The specified adapter is not an adapter application. Check the application type.%r<br /><br /> Adapter: %1 |

## Explanation  
 This Warning event indicates that the specified adapter is not an adapter application.  

## User Action  
 To resolve this warning, do the following:  

- Use the SSO Admin MMC Snap-In, right click the specified adapter, and then click Properties to determine the application type or use the command line tool  ssops -list and ssops -display to determine the application type.  

- Use the SSO Admin MMC Snap-In or ssops -addapp to set the adapter application.  

  For more information, see the following resources:  

- [How to Administer Password Synchronization](../core/how-to-administer-password-synchronization.md)
