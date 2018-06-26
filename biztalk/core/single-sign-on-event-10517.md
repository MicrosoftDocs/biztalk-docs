---
title: "Single Sign-On: Event 10517 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2b63e4b0-0ef6-45c2-b8b1-55ac20e79e26
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10517
## Details  

|                 |                                                                                                                                                                                                                                                                                                                             |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                                                  Enterprise Single Sign-On                                                                                                                                                  |
| Product Version |                                                                                                                                 [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                                  |
|    Event ID     |                                                                                                                                                            10517                                                                                                                                                            |
|  Event Source   |                                                                                                                                                           ENTSSO                                                                                                                                                            |
|    Component    |                                                                                                                                                             N\A                                                                                                                                                             |
|  Symbolic Name  |                                                                                                                                                   SSO_ERROR_BAD_SSO_ADMIN                                                                                                                                                   |
|  Message Text   | The SSO Administrators account is not valid. If it is a local account check that this account exists on the server. If it is a domain account contact your domain administrator. Enable SSO when the account is valid.%r<br /><br /> SSO Administrators: %1%r<br /><br /> Invalid accounts: %2%r<br /><br /> Error Code: %3 |

## Explanation  
 This Error event indicates that the SSO Administrators account specified for Enterprise Single Sign-On is not a valid Windows account. The service account running the Enterprise Single Sign-On service must be a member of this account. The SSO Administrators account can be either a Windows group account or an individual account. The SSO Administrators account can also be either a domain or local group account. When using an individual account, you cannot change this account to another individual account.  

## User Action  
 To resolve this error, do the following:  

- Verify the SSO Administrators account exists.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [SSO User Groups](../core/sso-user-groups.md)
