---
title: "Single Sign-On: Event 10527 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 40995ad8-9f74-4e96-863d-427e23025ba1
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10527
## Details  

|                 |                                                                                                                                                                                                     |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                      Enterprise Single Sign-On                                                                                      |
| Product Version |                                                                     [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                      |
|    Event ID     |                                                                                                10527                                                                                                |
|  Event Source   |                                                                                               ENTSSO                                                                                                |
|    Component    |                                                                                                  0                                                                                                  |
|  Symbolic Name  |                                                                                     SSO_ERROR_GET_SECRET_FAILED                                                                                     |
|  Message Text   | A request to get a master secret failed.%r<br /><br /> Secret Number: %1%r<br /><br /> Client User: %2%r<br /><br /> Client Computer: %3%r<br /><br /> Tracking ID: %4%r<br /><br /> Error Code: %5 |

## Explanation  
 This Error event indicates that a request to get the master secret has failed. In these cases there should be related messages in the Application event log.  

## User Action  
 To resolve this error, do the following:  

- Check the Application event log for associated events or errors.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [How to Generate the Master Secret](../core/how-to-generate-the-master-secret.md)  

- [Managing the Master Secret](../core/managing-the-master-secret.md)
