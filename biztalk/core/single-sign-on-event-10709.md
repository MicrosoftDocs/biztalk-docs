---
description: "Learn more about: Single Sign-On: Event 10709"
title: "Single Sign-On: Event 10709"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10709
## Details  

| Field | Error Details |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                  Enterprise Single Sign-On                                                                                                                   |
| Product Version |                                                                                                  [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                  |
|    Event ID     |                                                                                                                            10709                                                                                                                             |
|  Event Source   |                                                                                                                            ENTSSO                                                                                                                            |
|    Component    |                                                                                                                             N\A                                                                                                                              |
|  Symbolic Name  |                                                                                                                SSO_WARN_PS_PCNS_ACCESS_DENIED                                                                                                                |
|  Message Text   | Windows password changes from PCNS will only be accepted from Domain Controllers in the access domain.%r<br /><br /> Tracking ID: %1%r<br /><br /> Client User: %2%r<br /><br /> Access Domain: %3%r<br /><br /> Access Sid: %4%r<br /><br /> Error Code: %5 |

## Explanation  
 This Warning event indicates that a Windows password change was received from Password Change Notification Services (PCNS) on a server outside the ENTSSO server's domain. Windows password changes will only be accepted from domain controllers in the same domain as the ENTSSO server.  

## User Action  
 To resolve this warning, do the following:  

- Configure an ENTSSO server in the same domain as PCNS.  

  For more information, see the following resources:  

- [Password Synchronization](../core/password-synchronization2.md)
