---
description: "Learn more about: Single Sign-On: Event 10516"
title: "Single Sign-On: Event 10516"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10516
## Details  

| Field | Error Details |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                                                            Enterprise Single Sign-On                                                                                                                                                            |
| Product Version |                                                                                                                                           [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                                            |
|    Event ID     |                                                                                                                                                                      10516                                                                                                                                                                      |
|  Event Source   |                                                                                                                                                                     ENTSSO                                                                                                                                                                      |
|    Component    |                                                                                                                                                                       N\A                                                                                                                                                                       |
|  Symbolic Name  |                                                                                                                                                           SSO_ERROR_BAD_SSO_APP_ADMIN                                                                                                                                                           |
|  Message Text   | The SSO Affiliate Administrators account is not valid. If it is a local account check that this account exists on the server. If it is a domain account contact your domain administrator. Enable SSO when the account is valid.%r<br /><br /> SSO Affiliate Administrators: %1%r<br /><br /> Invalid accounts: %2%r<br /><br /> Error Code: %3 |

## Explanation  
 This Error event indicates that the SSO Affiliate Administrator account or group created by Enterprise Sing Sign-on is not a valid Windows account. The SSO Affiliate Administrators account can be either a Windows group account or an individual account. The SSO Affiliate Administrator account can also be either a domain or local group account.  

## User Action  
 To resolve this error, do the following:  

- Verify the SSO Affiliate Administrator account exists.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [SSO User Groups](../core/sso-user-groups.md)  

- [How to Update the SSO Database](../core/how-to-update-the-sso-database.md)
