---
description: "Learn more about: Single Sign-On: Event 10747"
title: "Single Sign-On: Event 10747"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10747
## Details  

| Field | Error Details |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                       Enterprise Single Sign-On                                                        |
| Product Version |                                       [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                       |
|    Event ID     |                                                                 10747                                                                  |
|  Event Source   |                                                                  N\A                                                                   |
|    Component    |                                                                  N\A                                                                   |
|  Symbolic Name  |                                                     SSO_ERROR_UNKNOWN_NOTIFICATION                                                     |
|  Message Text   | An unknown notification type was received.%r<br /><br /> Tracking ID: %1%r<br /><br /> Adapter: %2%r<br /><br /> Notification Type: %3 |

## Explanation  
 This Error event indicates that an internal error with an invalid notification type was detected by the SSO service.  

## User Action  
 To resolve this error, do the following:  

- Check the system and application event logs for associated events.  

  For more information, see the following resources:  

- [Using SSO](../core/using-sso.md)
