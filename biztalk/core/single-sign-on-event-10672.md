---
description: "Learn more about: Single Sign-On: Event 10672"
title: "Single Sign-On: Event 10672"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10672
## Details  

| Field | Error Details |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                                                                                           Enterprise Single Sign-On                                                                                                                                                                                            |
| Product Version |                                                                                                                                                                           [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                                                                           |
|    Event ID     |                                                                                                                                                                                                     10672                                                                                                                                                                                                      |
|  Event Source   |                                                                                                                                                                                                     ENTSSO                                                                                                                                                                                                     |
|    Component    |                                                                                                                                                                                                      N\A                                                                                                                                                                                                       |
|  Symbolic Name  |                                                                                                                                                                                 SSO_WARN_EXTERNAL_MAPPING_CONFLICT_NOT_ALLOWED                                                                                                                                                                                 |
|  Message Text   | A Windows password change would have caused changes to more than one account on the same external system.%r<br /><br /> This has been prevented because the adapter for this external system is configured to not allow mapping conflicts.%r<br /><br /> Tracking ID: %1%r<br /><br /> Adapter: %2%r<br /><br /> Windows Account: %3%r<br /><br /> External Account 1: %4%r<br /><br /> External Account 2: %5 |

## Explanation  
 This Warning event indicates that a Windows password change would have caused changes to more than one account on the same external system. This change was prevented because the adapter configuration would not allow it.  

## User Action  

-   Use the SSO Admin tools to configure the **Allow Mapping Conflicts** property for the Password Sync Adapter.  

## More info

- **Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]

- [Password Synchronization](../core/password-synchronization2.md)
