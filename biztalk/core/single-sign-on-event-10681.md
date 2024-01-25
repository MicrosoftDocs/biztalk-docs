---
description: "Learn more about: Single Sign-On: Event 10681"
title: "Single Sign-On: Event 10681"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10681
## Details  

| Field | Error Details |
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
