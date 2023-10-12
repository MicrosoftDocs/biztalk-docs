---
description: "Learn more about: Single Sign-On: Event 10673"
title: "Single Sign-On: Event 10673"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10673
## Details  

| Field | Error Details |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                                                                        Enterprise Single Sign-On                                                                                                                                                                         |
| Product Version |                                                                                                                                                        [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                                                        |
|    Event ID     |                                                                                                                                                                                  10673                                                                                                                                                                                   |
|  Event Source   |                                                                                                                                                                                  ENTSSO                                                                                                                                                                                  |
|    Component    |                                                                                                                                                                                   N\A                                                                                                                                                                                    |
|  Symbolic Name  |                                                                                                                                                                SSO_INFO_WINDOWS_MAPPING_CONFLICT_ALLOWED                                                                                                                                                                 |
|  Message Text   | An external password change will cause changes to more than one Windows account.%r<br /><br /> This is allowed because the adapter for this external system is configured to allow mapping conflicts.%r<br /><br /> Tracking ID: %1%r<br /><br /> Adapter: %2%r<br /><br /> External Account: %3%r<br /><br /> Windows Account 1: %4%r<br /><br /> Windows Account 2: %5 |

## Explanation  
 This Information event indicates that an external password change will cause changes to more than one Windows account.  

## User Action  

-   No user action is necessary.  

## More info

- [How to Administer Password Synchronization](../core/how-to-administer-password-synchronization.md)  

- **Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]

- [Password Synchronization](../core/password-synchronization2.md)
