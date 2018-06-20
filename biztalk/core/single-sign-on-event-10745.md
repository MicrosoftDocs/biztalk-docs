---
title: "Single Sign-On: Event 10745 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ed630e40-d876-4e90-937e-4d2d54fe9f1a
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10745
## Details  

|                 |                                                                                                                                              |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                          Enterprise Single Sign-On                                                           |
| Product Version |                                          [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                          |
|    Event ID     |                                                                    10745                                                                     |
|  Event Source   |                                                                    ENTSSO                                                                    |
|    Component    |                                                                     N\A                                                                      |
|  Symbolic Name  |                                                          SSO_ERROR_ADAPTER_OFFLINE                                                           |
|  Message Text   | The adapter is offline.%r<br /><br /> Tracking ID: %1%r<br /><br /> Adapter: %2%r<br /><br /> Error Message: %3%r<br /><br /> Error Code: %4 |

## Explanation  
 This Error event indicates that the specified adapter is offline.  

## User Action  
 To resolve this error, do one or more of the following:  

- Check the system and application event logs for associated errors.  

- Check the external adapter for errors.  

  For more information, see the following resources:  

- [How to Administer Password Synchronization](../core/how-to-administer-password-synchronization.md)
