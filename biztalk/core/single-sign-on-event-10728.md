---
title: "Single Sign-On: Event 10728 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f579189c-c9a5-4d2c-a3d5-f0ba03c5a3ef
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10728
## Details  

|                 |                                                                                                                                                                                                                                                                   |
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
