---
title: "Single Sign-On: Event 10611 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4549ac01-b828-478f-aea0-862e14fac149
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10611
## Details  
  
|                 |                                                                                                                                                                                                                                           |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                         Enterprise Single Sign-On                                                                                                         |
| Product Version |                                                                                        [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                         |
|    Event ID     |                                                                                                                   10611                                                                                                                   |
|  Event Source   |                                                                                                                  ENTSSO                                                                                                                   |
|    Component    |                                                                                                                    N/A                                                                                                                    |
|  Symbolic Name  |                                                                                                     SSO_INFO_SERVICE_STARTING_NO_SSL                                                                                                      |
|  Message Text   | The SSO service is starting.%r<br /><br /> Computer Name: %1%r<br /><br /> SQL Server Name: %2%r<br /><br /> SSO Database Name: %3%r<br /><br /> Not using SSL. See documentation for details on how to secure the SQL Server connection. |
  
## Explanation  
 The ENTSSO Service is starting without using Secure Sockets Layer (SSL). It is recommended that you secure your connection from the SSO Service to SQL.  
  
## User Action  
 See the documentation at [How to Enable SSL for SSO](../core/how-to-enable-ssl-for-sso.md)  
  
 .