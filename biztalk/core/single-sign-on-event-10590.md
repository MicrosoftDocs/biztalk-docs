---
description: "Learn more about: Single Sign-On: Event 10590"
title: "Single Sign-On: Event 10590"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10590
## Details  
  
| Field | Error Details|
|-----------------|------------------------------------------------------------|
|  Product Name   |                 Enterprise Single Sign-On                  |
| Product Version | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    Event ID     |                           10590                            |
|  Event Source   |                           ENTSSO                           |
|    Component    |                            N/A                             |
|  Symbolic Name  |                  SSO_ERROR_OUT_OF_SERVICE                  |
|  Message Text   |        Enterprise Single Sign-On is going offline.         |
  
## Explanation  
 The ENTSSO system usually checks for updates on the ENTSSO database every 30 seconds. If the database is unavailable for a specified time (usually five minutes), the system itself goes offline. In this state the system will not respond to requests for credentials. Some offline and administrative activities are still possible.  
  
## User Action  
 This error indicates that the ENTSSO database is offline. You should investigate immediately.
