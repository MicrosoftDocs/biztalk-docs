---
description: "Learn more about: Single Sign-On: Event 10521"
title: "Single Sign-On: Event 10521"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10521
## Details  

| Field | Error Details |
|-----------------|-----------------------------------------------------------------------|
|  Product Name   |                       Enterprise Single Sign-On                       |
| Product Version |      [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]       |
|    Event ID     |                                 10521                                 |
|  Event Source   |                                ENTSSO                                 |
|    Component    |                                  N\A                                  |
|  Symbolic Name  |                     SSO_ERROR_SECRETS_NOT_LOADED                      |
|  Message Text   | Could not load secrets from the registry of the master secret server. |

## Explanation  
 This Error event occurs on the master secret server when the master secrets cannot be obtained from the registry. There may be related errors messages in the event log with further information. The most likely cause of this is that there has been a permissions error or an encryption error when the SSO service account attempted to access the registry. This can occur when the SSO service account has been changed. The master secret is encrypted with a key that is based on the identity of the SSO service account. If that account is changed, then the existing master secret in the registry can no longer be decrypted.  

## User Action  
 To resolve this error, do the following:  

- Change the SSO service account by backing-up the master secret, then changing the SSO service account, and then restoring the master secret. This can restore the master secret and should fix this error.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [Master Secret Server](../core/master-secret-server.md)  

- [Managing the Master Secret](../core/managing-the-master-secret.md)  

- [Configuring SSO](../core/configuring-sso.md)  

- [SSO Security Recommendations](../core/sso-security-recommendations.md)
