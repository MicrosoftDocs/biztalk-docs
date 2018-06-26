---
title: "Single Sign-On: Event 10532 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ae2112bc-b53c-4d99-9dc1-a2f55dda4665
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10532
## Details  

|                 |                                                                                                                                                                                     |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                              Enterprise Single Sign-On                                                                              |
| Product Version |                                                             [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                              |
|    Event ID     |                                                                                        10532                                                                                        |
|  Event Source   |                                                                                       ENTSSO                                                                                        |
|    Component    |                                                                                         CO                                                                                          |
|  Symbolic Name  |                                                                             SSO_WARN_LOST_SECRET_SERVER                                                                             |
|  Message Text   | Failed to retrieve master secrets. Verify that the master secret server name is correct and that it is available.%r<br /><br /> Secret Server Name: %1%r<br /><br /> Error Code: %2 |

## Explanation  
 This Warning event indicates that a request to get the master secret has failed. This might be because the Enterprise Single Sign-On service is not running on the server.  

## User Action  
 To resolve this warning, do one or more of the following:  

- Check the Application event log for associated events or errors.  

- Verify the master secret server name is correct.  

- Verify the master secret server is online and that the Enterprise Single Sign-On service is running.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [How to Generate the Master Secret](../core/how-to-generate-the-master-secret.md)  

- [Managing the Master Secret](../core/managing-the-master-secret.md)
