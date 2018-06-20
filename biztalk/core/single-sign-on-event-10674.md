---
title: "Single Sign-On: Event 10674 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ad0c0d9e-1e6d-4c3e-86e0-9e336a18f3d6
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10674
## Details  

|                 |                                                                                                                                                                                                                                                                                                                                                                                             |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                                                                                  Enterprise Single Sign-On                                                                                                                                                                                  |
| Product Version |                                                                                                                                                                 [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                                                                  |
|    Event ID     |                                                                                                                                                                                            10674                                                                                                                                                                                            |
|  Event Source   |                                                                                                                                                                                           ENTSSO                                                                                                                                                                                            |
|    Component    |                                                                                                                                                                                             N\A                                                                                                                                                                                             |
|  Symbolic Name  |                                                                                                                                                                        SSO_WARN_WINDOWS_MAPPING_CONFLICT_NOT_ALLOWED                                                                                                                                                                        |
|  Message Text   | An external password change would have caused changes to more than one Windows account.%r<br /><br /> This has been prevented because the adapter for this external system is configured to not allow mapping conflicts.%r<br /><br /> Tracking ID: %1%r<br /><br /> Adapter: %2%r<br /><br /> External Account: %3%r<br /><br /> Windows Account 1: %4%r<br /><br /> Windows Account 2: %5 |

## Explanation  
 This Warning event indicates that an external password change would have caused changes to more than one Windows account. This change was prevented because the adapter configuration would not allow it.  

## User Action  
 To resolve this error, do the following:  

-   If mapping conflicts are expected and allowed, use the SSO Admin tools to configure the **Allow Mapping Conflicts** property for the Password Sync Adapter.  

## More info

- **Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]

- [Password Synchronization](../core/password-synchronization2.md)
