---
description: "Learn more about: Single Sign-On: Event 10679"
title: "Single Sign-On: Event 10679"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10679
## Details  

| Field | Error Details |
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
