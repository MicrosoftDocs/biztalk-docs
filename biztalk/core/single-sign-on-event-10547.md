---
description: "Learn more about: Single Sign-On: Event 10547"
title: "Single Sign-On: Event 10547"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10547
## Details  

| Field | Error Details |
|-----------------|---------------------------------------------------------------------------|
|  Product Name   |                         Enterprise Single Sign-On                         |
| Product Version |        [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]         |
|    Event ID     |                                   10547                                   |
|  Event Source   |                                  ENTSSO                                   |
|    Component    |                                    CO                                     |
|  Symbolic Name  |                          SSO_WARN_UPDATE_FAILED                           |
|  Message Text   | Failed to update the credentials in the SSO database during re-encryption |

## Explanation  
 This Warning event indicates that it was not possible to update the credentials with the result of the new encryption. When the master secret is changed, either by generating a new secret or by restoring an old secret, a re-encryption is performed on the SSO database to decrypt all the secrets encrypted with the old secret, and re-encrypt them with the new secret. This event can occur if the credentials were deleted as they were in the process of being re-encrypted.  

## User Action  
 To resolve this warning, do the following:  

- Wait for another re-encryption to occur after a short delay; if that does not occur automatically, restart the SSO service which will trigger a new re-encryption if one is required.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [Understanding SSO](../core/understanding-sso.md)
