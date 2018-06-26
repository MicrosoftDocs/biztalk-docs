---
title: "Single Sign-On: Event 10679 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 645f2b74-2cbe-4c6a-b0f5-7e31f93f88c6
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10679
## Details  

|                 |                                                                                                                                                                                                                                                |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                           Enterprise Single Sign-On                                                                                                            |
| Product Version |                                                                                           [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                           |
|    Event ID     |                                                                                                                     10679                                                                                                                      |
|  Event Source   |                                                                                                                     ENTSSO                                                                                                                     |
|    Component    |                                                                                                                      N\A                                                                                                                       |
|  Symbolic Name  |                                                                                                          SSO_WARN_PS_MAPPING_DISABLED                                                                                                          |
|  Message Text   | External password change. The password was not changed for the external account because the mapping is disabled.%r<br /><br /> Tracking ID: %1%r<br /><br /> Adapter: %2%r<br /><br /> Application Name: %3%r<br /><br /> External Account: %4 |

## Explanation  
 This Warning event indicates that the password was not changed for the external account because the mapping is disabled.  

## User Action  
 To resolve this warning do the following:  

-   Use the SSO administration tools to enable mapping for this adapter.  

## More info

- [Password Synchronization](../core/password-synchronization2.md)  

- **Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
