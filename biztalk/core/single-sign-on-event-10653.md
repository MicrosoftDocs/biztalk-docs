---
description: "Learn more about: Single Sign-On: Event 10653"
title: "Single Sign-On: Event 10653"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10653
## Details  

| Field | Error Details |
|-----------------|------------------------------------------------------------|
|  Product Name   |                 Enterprise Single Sign-On                  |
| Product Version | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    Event ID     |                           10653                            |
|  Event Source   |                           ENTSSO                           |
|    Component    |                            N\A                             |
|  Symbolic Name  |        SSO_ERROR_PS_ADAPTER_CALLBACK_ACCESS_DENIED         |
|  Message Text   |    Password sync server (for adapters) access denied.%r    |

## Explanation  
 This Error event indicates that a client attempted to contact the server but the call was refused. This can be caused by a number of different reasons, such as incorrect protocol or insufficient security permissions.  

## User Action  
 To resolve this error, do the following:  

- Note the information in this message, and any relevant information in the event log, and contact Microsoft Product Support Services.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [Password Synchronization](../core/password-synchronization2.md)
