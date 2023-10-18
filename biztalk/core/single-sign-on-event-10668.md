---
description: "Learn more about: Single Sign-On: Event 10668"
title: "Single Sign-On: Event 10668"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10668
## Details  

| Field | Error Details |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                                                   Enterprise Single Sign-On                                                                                                                                                   |
| Product Version |                                                                                                                                  [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                                   |
|    Event ID     |                                                                                                                                                             10668                                                                                                                                                             |
|  Event Source   |                                                                                                                                                            ENTSSO                                                                                                                                                             |
|    Component    |                                                                                                                                                              N\A                                                                                                                                                              |
|  Symbolic Name  |                                                                                                                                               SSO_WARN_NO_OLD_WINDOWS_PASSWORD                                                                                                                                                |
|  Message Text   | Cannot change the Windows password because the old Windows password for this account is not available in the SSO database.%r<br /><br /> Use the SSO administration tools to set the external credentials for this Windows account.%r<br /><br /> Tracking ID: %1%r<br /><br /> Adapter: %2%r<br /><br /> Windows Account: %3 |

## Explanation  
 This Warning event indicates that Password Sync cannot change the Windows password because the old Windows password for this account is not available in the SSO database.  

## User Action  
 To resolve this warning, do the following:  

-   Determine which Applications were assigned to this Adapter (name in event log message) and then use the SSO administration tools to set the external credentials for this Windows account. You must set the external password (for the given Windows Account) in all of those Applications.  

## More info

- [Password Synchronization](../core/password-synchronization2.md)  

- **Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
