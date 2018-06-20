---
title: "Single Sign-On: Event 10665 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8d0de9d0-9b46-4f3a-b796-1ce3de01cf4c
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10665
## Details  

|                 |                                                                                                                        |
|-----------------|------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                               Enterprise Single Sign-On                                                |
| Product Version |                               [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                               |
|    Event ID     |                                                         10665                                                          |
|  Event Source   |                                                         ENTSSO                                                         |
|    Component    |                                                          N\A                                                           |
|  Symbolic Name  |                                                 SSO_WARN_NO_PROPERTIES                                                 |
|  Message Text   | Error reading password sync adapter properties. Using defaults.%r<br /><br /> Adapter: %1%r<br /><br /> Error Code: %2 |

## Explanation  
 This Warning event indicates that there was an error reading the default password sync adapter properties. Each password sync adapter has configuration properties associated with it. These properties are stored in the SSO config store and are created by the SSO command line tools or the SSO Admin MMC when the password sync adapter is created.  There can be missing properties if the password sync adapter was created by any other means, then this error can be issued.  

## User Action  
 To resolve this warning, do one or more of the following:  

-   Verify password sync adapter properties.  

-   Recreate the password sync adapter  

## More info

- **Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]

- [Password Synchronization](../core/password-synchronization2.md)
