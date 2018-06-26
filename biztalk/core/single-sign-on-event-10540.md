---
title: "Single Sign-On: Event 10540 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ce91ff30-3d68-4c5f-a955-5c426e94d917
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10540
## Details  

|                 |                                                                                  |
|-----------------|----------------------------------------------------------------------------------|
|  Product Name   |                            Enterprise Single Sign-On                             |
| Product Version |            [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]            |
|    Event ID     |                                      10540                                       |
|  Event Source   |                                      ENTSSO                                      |
|    Component    |                                        CO                                        |
|  Symbolic Name  |                         SSO_WARN_APP_TICKETS_NOT_ALLOWED                         |
|  Message Text   | Tickets are not enabled for this application.%r<br /><br /> Application Name: %1 |

## Explanation  
 This Warning event indicates that the tickets feature has not been enabled for this application. The use of SSO tickets is an optional feature for each SSO application.  

## User Action  
 To resolve this warning, do the following:  

- Contact your Application Administrator to enable tickets for this SSO application. This can be done using the SSO administration tools (GUI or command line).  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [SSO Tickets](../core/sso-tickets.md)  

- [How to List the Properties of an Affiliate Application](../core/how-to-list-the-properties-of-an-affiliate-application.md)  

- [How to Update the Properties of an Affiliate Application](../core/how-to-update-the-properties-of-an-affiliate-application.md)
