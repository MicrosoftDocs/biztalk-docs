---
title: "Single Sign-On: Event 10681 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 87ce2e50-cf54-4b23-b247-f137ce64ba1d
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10681
## Details  

|                 |                                                                                                                                                                                                                      |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                              Enterprise Single Sign-On                                                                                               |
| Product Version |                                                                              [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                              |
|    Event ID     |                                                                                                        10681                                                                                                         |
|  Event Source   |                                                                                                        ENTSSO                                                                                                        |
|    Component    |                                                                                                         N\A                                                                                                          |
|  Symbolic Name  |                                                                                         SSO_WARN_NO_WINDOWS_PASSWORD_CHANGE                                                                                          |
|  Message Text   | External password change. The Windows password was not changed because one or more of the external account changes failed.%r<br /><br /> Tracking ID: %1%r<br /><br /> Adapter: %2%r<br /><br /> Windows Account: %3 |

## Explanation  
 This Warning event indicates that the Windows password was not changed because one or more of the external account changes failed.  

## User Action  
 To resolve this warning, do one or more of the following:  

-   Check the System and Application Event logs for associated events.  

-   Verify adapter configuration using the SSO administration tools.  

-   Verify external systems.  

## More info

- [Password Synchronization](../core/password-synchronization2.md)  

- **Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
