---
description: "Learn more about: Single Sign-On: Event 10584"
title: "Single Sign-On: Event 10584"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10584
## Details  
  
| Field | Error Details|
|-----------------|----------------------------------------------------------------|
|  Product Name   |                   Enterprise Single Sign-On                    |
| Product Version |   [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]   |
|    Event ID     |                             10584                              |
|  Event Source   |                             ENTSSO                             |
|    Component    |                              N/A                               |
|  Symbolic Name  |                   SSO_WARN_NO_IMPERSONATION                    |
|  Message Text   | Could not impersonate the client.%r<br /><br /> Error Code: %1 |
  
## Explanation  
 Impersonating the client is something the ENTSSO System does to verify the client’s identity. When the system is unable to impersonate a client, one of three things may have occurred. The client may be attempting to perform an usual activity, the client may be attempting to infiltrate system security, or the client application may have been designed to block impersonation.  
  
## User Action  
 Locate the client application and determine what it is attempting to do, and whether or not it is blocking impersonation.
