---
description: "Learn more about: Single Sign-On: Event 10515"
title: "Single Sign-On: Event 10515"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10515
## Details  
  
| Field | Error Details |
|-----------------|-------------------------------------------------------------------------------|
|  Product Name   |                           Enterprise Single Sign-On                           |
| Product Version |          [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]           |
|    Event ID     |                                     10515                                     |
|  Event Source   |                                    ENTSSO                                     |
|    Component    |                                      N\A                                      |
|  Symbolic Name  |                            SSO_ERROR_POLL_DATABASE                            |
|  Message Text   | Lost contact with the SSO database. Check that the SSO database is available. |
  
## Explanation  
 This Error event indicates that the SSO Service has lost contact with the SSO database.  
  
## User Action  
 To resolve this error, do one or more of the following:  
  
- Verify that the SQL Server (MSSQLSERVER) service is running.  
  
- Verify network connectivity to SQL Server if on a remote server.  
  
  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  
  
- [Implementing Enterprise Single Sign-On](../core/implementing-enterprise-single-sign-on.md)  
  
- [How to Display the SSO Database Information](../core/how-to-display-the-sso-database-information.md)  
  
- [Configuring SSO](../core/configuring-sso.md)  
  
  See also SQL Server Books Online
