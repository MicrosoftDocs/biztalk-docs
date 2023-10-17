---
description: "Learn more about: Single Sign-On: Event 11016"
title: "Single Sign-On: Event 11016"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 11016
## Details  
  
| Field | Error Details|
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                                                                   Enterprise Single Sign-On                                                                                                                                                                    |
| Product Version |                                                                                                                                                   [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                                                   |
|    Event ID     |                                                                                                                                                                             11016                                                                                                                                                                              |
|  Event Source   |                                                                                                                                                                             ENTSSO                                                                                                                                                                             |
|    Component    |                                                                                                                                                                              N/A                                                                                                                                                                               |
|  Symbolic Name  |                                                                                                                                                                RPC EXTENDED ERROR INFORMATION%r                                                                                                                                                                |
|  Message Text   | %1%r<br /><br /> Error Code: %2<br /><br /> The AuthzInitializeContextFromSid function failed with ERROR_ACCESS_DENIED. This means that the service account that the SSO server is running under does not have sufficient permissions to check group membership in Active Directory. Please check your documentation for details on how to fix this problem.%r |
  
## Explanation  
 The service account that the SSO server is running under does not have sufficient permissions to check group membership in Active Directory.  
  
## User Action  
 See [SSO Server](../core/sso-server.md) in the SSO documentation.
