---
title: "Single Sign-On: Event 10538 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1211ac33-9149-4dd3-85a2-d46eb24d1060
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10538
## Details  

|                 |                                                                           |
|-----------------|---------------------------------------------------------------------------|
|  Product Name   |                         Enterprise Single Sign-On                         |
| Product Version |        [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]         |
|    Event ID     |                                   10538                                   |
|  Event Source   |                                  ENTSSO                                   |
|    Component    |                                    CO                                     |
|  Symbolic Name  |                           SSO_WARN_APP_DISABLED                           |
|  Message Text   | The application is currently disabled.%r<br /><br /> Application Name: %1 |

## Explanation  
 This Warning event indicates that the SSO affiliate application has been disabled by an Application Administrator.  

## User Action  
 To resolve this warning, do one or more of the following:  

- Contact your Application Administrator to enable the SSO affiliate application. This can be done using the SSO administration tools (GUI or command line).  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [How to Enable an Affiliate Application](../core/how-to-enable-an-affiliate-application.md)  

- [How to Disable an Affiliate Application](../core/how-to-disable-an-affiliate-application.md)
