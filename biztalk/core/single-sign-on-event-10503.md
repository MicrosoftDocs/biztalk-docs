---
description: "Learn more about: Single Sign-On: Event 10503"
title: "Single Sign-On: Event 10503"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10503
## Details  

| Field | Error Details |
|-----------------|---------------------------------------------------------------|
|  Product Name   |                   Enterprise Single Sign-On                   |
| Product Version |  [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]   |
|    Event ID     |                             10503                             |
|  Event Source   |                            ENTSSO                             |
|    Component    |                              N\A                              |
|  Symbolic Name  |                SSO_ERROR_SERVICE_START_FAILED                 |
|  Message Text   | The SSO service failed to start.%r<br /><br /> Error Code: %1 |

## Explanation  
 This Error event indicates that the ENTSSO Service could not start due to an exception.  

## User Action  
 To resolve this error, do the following:  

- Check both the Application and System event logs for related errors from ENTSSO or other services.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [Using SSO](../core/using-sso.md)
