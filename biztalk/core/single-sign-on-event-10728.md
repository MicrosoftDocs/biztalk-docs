---
description: "Learn more about: Single Sign-On: Event 10728"
title: "Single Sign-On: Event 10728"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10728
## Details  

| Field | Error Details |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                     Enterprise Single Sign-On                                                                                                                     |
| Product Version |                                                                                                    [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                     |
|    Event ID     |                                                                                                                               10728                                                                                                                               |
|  Event Source   |                                                                                                                              ENTSSO                                                                                                                               |
|    Component    |                                                                                                                                N\A                                                                                                                                |
|  Symbolic Name  |                                                                                                                         SSO_ERROR_VERSION                                                                                                                         |
|  Message Text   | This version of the SSO server is not compatible with the SSO database. Please upgrade your master secret server.%r<br /><br /> SQL Server Name: %1%r<br /><br /> SSO Database Name: %2%r<br /><br /> SSO Database Version: %3%r<br /><br /> Required Version: %4 |

## Explanation  
 This Error event indicates that the SSO server version is more recent than (the version that originally created) the SSO database.  

## User Action  
 To resolve this error, do the following:  

- Upgrade the SSO master secret server to match the current version of this SSO server. This will upgrade the SSO database to the current version.  

  For more information, see the following resources:  

- [Managing the Master Secret](../core/managing-the-master-secret.md)
