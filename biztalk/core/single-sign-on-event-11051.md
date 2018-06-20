---
title: "Single Sign-On: Event 11051 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fe767818-f74e-415c-9287-5b7cc46e358a
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 11051
## Details  
  
|                 |                                                                                                                                                                                                                                                                                                                                              |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                                                          Enterprise Single Sign-On                                                                                                                                                           |
| Product Version |                                                                                                                                          [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                                          |
|    Event ID     |                                                                                                                                                                    11051                                                                                                                                                                     |
|  Event Source   |                                                                                                                                                                    ENTSSO                                                                                                                                                                    |
|    Component    |                                                                                                                                                                     N/A                                                                                                                                                                      |
|  Symbolic Name  |                                                                                                                                                         SSO_WARN_SSO_ADMIN_NOT_GROUP                                                                                                                                                         |
|  Message Text   | The SSO Administrators account contains one or more individual (not group) accounts. If these individual accounts are deleted from Active Directory or the local computer they must be promptly removed from the SSO system or they could become a security risk.%r<br /><br /> SSO Administrators: %1%r<br /><br /> Individual accounts: %2 |
  
## Explanation  
 Deleting an individual account from the Active Directory or local computer does not automatically delete that account from the SSO System. This means that if the account USER1 was deleted locally, and then a different user (for instance, a new employee) joined the system using that same name, the SSO System would grant the new USER1 all security rights possessed by the original USER1. This poses a security risk.  
  
## User Action  
 No action is necessary until an individual account is deleted from Active Directory or the local computer. At that point, you must delete the individual account from the SSO System as soon as possible.