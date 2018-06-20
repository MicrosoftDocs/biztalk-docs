---
title: "Single Sign-On: Event 10680 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 88ea12ff-d181-423f-9054-b0c656cc4558
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10680
## Details  

|                 |                                                                                                                                                                                                                                                                                                         |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                                        Enterprise Single Sign-On                                                                                                                                        |
| Product Version |                                                                                                                       [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                        |
|    Event ID     |                                                                                                                                                  10680                                                                                                                                                  |
|  Event Source   |                                                                                                                                                 ENTSSO                                                                                                                                                  |
|    Component    |                                                                                                                                                   N\A                                                                                                                                                   |
|  Symbolic Name  |                                                                                                                                      SSO_WARN_PS_GET_CREDS_FAILED                                                                                                                                       |
|  Message Text   | The password was not changed for the external account because the existing external credentials could not be obtained from the SSO database.%r<br /><br /> Tracking ID: %1%r<br /><br /> Adapter: %2%r<br /><br /> Application Name: %3%r<br /><br /> External Account: %4%r<br /><br /> Error Code: %5 |

## Explanation  
 This Warning event indicates that the password was not changed for the external account because the existing external credentials could not be obtained from the SSO database.  

## User Action  
 To resolve this warning, do the following:  

-   Verify external credentials.  

-   The external credentials are not valid, use the SSO administration tools to set the external credentials for this external account. You must set the external password (for the given account) in all associated applications.  

## More info

- [Password Synchronization](../core/password-synchronization2.md)  

- **Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
