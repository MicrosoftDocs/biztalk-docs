---
title: "Single Sign-On: Event 10513 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b3306223-111f-4abf-ae65-be839b355216
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10513
## Details  

|                 |                                                                                      |
|-----------------|--------------------------------------------------------------------------------------|
|  Product Name   |                              Enterprise Single Sign-On                               |
| Product Version |              [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]              |
|    Event ID     |                                        10513                                         |
|  Event Source   |                                        ENTSSO                                        |
|    Component    |                                         N\A                                          |
|  Symbolic Name  |                              SSO_ERROR_DB_FIRST_ACCESS                               |
|  Message Text   | Failed to contact the SSO database: %1%r<br /><br /> %2%r<br /><br /> Error code: %3 |

## Explanation  
 This Error event indicates that the SSO Service cannot connect to the SSO database when it starts. The event message contains the Data Source Name (DSN) string indicating the specified SQL Server and database names as well as the error message that was returned from the SQL connection libraries.  

 When the SSO Service starts, it will attempt to connect to the SSO database using the SQL Server and SSO database names specified in the registry. The SSO Service will attempt to connect 12 times, waiting 5 seconds between each failed attempt, for a total of 1 minute.  

## User Action  
 To resolve this error, do one or more of the following:  

- Verify the SQL Server (MSSQLSERVER) service is running.  

- Verify the Data Source Name (DSN) string indicated in the error message is correct and contains the correct SQL Server and database names.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [Implementing Enterprise Single Sign-On](../core/implementing-enterprise-single-sign-on.md)  

- [How to Display the SSO Database Information](../core/how-to-display-the-sso-database-information.md)  

- [Configuring SSO](../core/configuring-sso.md)  

- SQL Server Books Online
