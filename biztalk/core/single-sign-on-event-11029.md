---
description: "Learn more about: Single Sign-On: Event 11029"
title: "Single Sign-On: Event 11029"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 11029
## Details  
  
| Field | Error Details|
|-----------------|----------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                              Enterprise Single Sign-On                                               |
| Product Version |                              [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                              |
|    Event ID     |                                                        11029                                                         |
|  Event Source   |                                                        ENTSSO                                                        |
|    Component    |                                                         N/A                                                          |
|  Symbolic Name  |                                               SSO_INFO_CASE_SENSITIVE                                                |
|  Message Text   | The SSO database is case sensitive. The SSO server will run in case sensitive mode. See documentation for details.%r |
  
## Explanation  
 By default the SSO server is not case-sensitive. However, the SQL Server SSO database has been configured to be case-sensitive, so the SSO Server will also run in case sensitive mode.  
  
## User Action  
 Be aware of this when specifying application names and external account names as they are now case-sensitive. For more information, see [SSO Server](../core/sso-server.md).
