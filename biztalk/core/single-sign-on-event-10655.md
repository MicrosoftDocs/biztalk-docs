---
title: "Single Sign-On: Event 10655 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1bb6a8dd-35e4-40a6-8900-450a9b6de249
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10655
## Details  

|                 |                                                                              |
|-----------------|------------------------------------------------------------------------------|
|  Product Name   |                          Enterprise Single Sign-On                           |
| Product Version |          [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]          |
|    Event ID     |                                    10655                                     |
|  Event Source   |                                    ENTSSO                                    |
|    Component    |                                     N\A                                      |
|  Symbolic Name  |                   SSO_ERROR_PS_PING_CALLBACK_ACCESS_DENIED                   |
|  Message Text   | Password sync server (for ping) access denied.%r<br /><br /> Client User: %1 |

## Explanation  
 This Error event indicates that a message was sent to the [name] server but the reply was blocked. This can be caused by a number of different reasons, such as incorrect protocol or insufficient security permissions on the server.  

## User Action  
 To resolve this error, do the following:  

- Note the information in this message, and any relevant information in the event log, and contact Microsoft Product Support Services.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [Password Synchronization](../core/password-synchronization2.md)
