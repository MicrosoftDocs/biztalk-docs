---
description: "Learn more about: Single Sign-On: Event 10671"
title: "Single Sign-On: Event 10671"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10671
## Details  

| Field | Error Details |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                                                                                  Enterprise Single Sign-On                                                                                                                                                                                  |
| Product Version |                                                                                                                                                                 [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                                                                  |
|    Event ID     |                                                                                                                                                                                            10671                                                                                                                                                                                            |
|  Event Source   |                                                                                                                                                                                           ENTSSO                                                                                                                                                                                            |
|    Component    |                                                                                                                                                                                             N\A                                                                                                                                                                                             |
|  Symbolic Name  |                                                                                                                                                                         SSO_INFO_EXTERNAL_MAPPING_CONFLICT_ALLOWED                                                                                                                                                                          |
|  Message Text   | A Windows password change will cause changes to more than one account on the same external system.%r<br /><br /> This is allowed because the adapter for this external system is configured to allow mapping conflicts.%r<br /><br /> Tracking ID: %1%r<br /><br /> Adapter: %2%r<br /><br /> Windows Account: %3%r<br /><br /> External Account 1: %4%r<br /><br /> External Account 2: %5 |

## Explanation  
 This Information event indicates that a Windows password change will cause changes to more than one account on the same external system.  

## User Action  

-   No user action is necessary.  

## More info

- **Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]

- [Password Synchronization](../core/password-synchronization2.md)
