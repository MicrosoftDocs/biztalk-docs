---
title: "Single Sign-On: Event 10715 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f63c98d2-988e-466f-be40-171b13a34732
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10715
## Details  

|                 |                                                                                                                                                                                                                  |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                            Enterprise Single Sign-On                                                                                             |
| Product Version |                                                                            [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                            |
|    Event ID     |                                                                                                      10715                                                                                                       |
|  Event Source   |                                                                                                      ENTSSO                                                                                                      |
|    Component    |                                                                                                       N\A                                                                                                        |
|  Symbolic Name  |                                                                                            SSO_WARN_NO_CREATE_ADAPTER                                                                                            |
|  Message Text   | The client user must be a member of the SSO Administrators account to create adapters.%r<br /><br /> Client User: %1%r<br /><br /> SSO Administrators: %2%r<br /><br /> Adapter: %3%r<br /><br /> Error Code: %4 |

## Explanation  
 This Warning event indicates that the client user must be a member of the SSO Administrators account to create adapters.  

## User Action  
 To resolve this warning, do the following:  

- Logon with an account that belongs to the SSO Administrators group.  

  For more information, see the following resources:  

- [SSO User Groups](../core/sso-user-groups.md)
