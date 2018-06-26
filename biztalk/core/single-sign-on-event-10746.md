---
title: "Single Sign-On: Event 10746 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8189120b-923a-4c88-937e-f06565bcac56
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10746
## Details  

|                 |                                                                                                                                               |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                           Enterprise Single Sign-On                                                           |
| Product Version |                                          [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                           |
|    Event ID     |                                                                     10746                                                                     |
|  Event Source   |                                                                    ENTSSO                                                                     |
|    Component    |                                                                      N\A                                                                      |
|  Symbolic Name  |                                                           SSO_WARN_PASSWORD_EXPIRED                                                           |
|  Message Text   | The password for the external account has expired.%r<br /><br /> Tracking ID: %1%r<br /><br /> Adapter: %2%r<br /><br /> External Account: %3 |

## Explanation  
 This Warning event indicates that the password for the external account has expired.  

## User Action  
 To resolve this warning, check the system and application event logs for associated errors.    

## More info
For more information, see the following resources:  

- **Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]  

- [Password Synchronization](../core/password-synchronization2.md)
