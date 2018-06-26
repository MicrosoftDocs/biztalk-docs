---
title: "Single Sign-On: Event 10550 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 73d63bc5-1e60-426c-a0d6-55c51dbb8d76
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10550
## Details  
  
|                 |                                                                                                                                                                                                               |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                           Enterprise Single Sign-On                                                                                           |
| Product Version |                                                                          [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                           |
|    Event ID     |                                                                                                     10550                                                                                                     |
|  Event Source   |                                                                                                    ENTSSO                                                                                                     |
|    Component    |                                                                                                      N/A                                                                                                      |
|  Symbolic Name  |                                                                                        SSO_ERROR_SERVICE_NOT_SSO_ADMIN                                                                                        |
|  Message Text   | The SSO service could not start because the service account it is running under is not a member of the SSO Administrators account.%r<br /><br /> SSO Administrators: %1%r<br /><br /> SSO Service Account: %2 |
  
## Explanation  
 The SSO service must be running under a service account that is a member of the SSO Administrators account.  
  
## User Action  
 For more information, see [How to Specify SSO Administrators and Affiliate Administrators Accounts](../core/how-to-specify-sso-administrators-and-affiliate-administrators-accounts.md).