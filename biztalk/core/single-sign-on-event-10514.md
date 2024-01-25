---
description: "Learn more about: Single Sign-On: Event 10514"
title: "Single Sign-On: Event 10514"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10514
## Details

| Field | Error Details |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                    Enterprise Single Sign-On                                                                                     |
| Product Version |                                                                    [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                    |
|    Event ID     |                                                                                              10514                                                                                               |
|  Event Source   |                                                                                              ENTSSO                                                                                              |
|    Component    |                                                                                               N\A                                                                                                |
|  Symbolic Name  |                                                                                       SSO_ERROR_DB_ACCESS                                                                                        |
|  Message Text   | An error occurred while attempting to access the SSO database.%r<br /><br /> Function: %1%r<br /><br /> File: %2%r<br /><br /> %3.%r<br /><br /> SQL Error code: %4%r<br /><br /> Error code: %5 |

## Explanation
 This Error event indicates that an error was received from SQL Server when attempting to access the SSO database.

## User Action
 To resolve this error, do one or more of the following:

- Verify that the SQL Server (MSSQLSERVER) service is running.

- Check the SQL Server error code using the Events and Errors Message Center at [https://go.microsoft.com/fwlink/?LinkID=20869](https://go.microsoft.com/fwlink/?LinkID=20869).

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:

- [Implementing Enterprise Single Sign-On](../core/implementing-enterprise-single-sign-on.md)

- [How to Display the SSO Database Information](../core/how-to-display-the-sso-database-information.md)

  See also SQL Server Books Online.
