---
title: "Single Sign-On: Event 10613 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7a87ca19-24a0-4cf8-984f-2f70d7b5018c
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10613
## Details  
  
|                 |                                                                                                                                |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                   Enterprise Single Sign-On                                                    |
| Product Version |                                   [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                   |
|    Event ID     |                                                             10613                                                              |
|  Event Source   |                                                             ENTSSO                                                             |
|    Component    |                                                              N/A                                                               |
|  Symbolic Name  |                                                     SSO_ERROR_RPC_CALLBACK                                                     |
|  Message Text   | SSO server access denied.%r<br /><br /> Client User: %1%r<br /><br /> RPC call information: %2:%3%r<br /><br /> Error Code: %4 |
  
## Explanation  
 A call was made from a client to the SSO Server but was not accepted. This can be caused by a number of different reasons, such as incorrect protocol or insufficient security permissions on the client.  
  
## User Action  
 Note the information in this message, and any relevant information in the event log, and contact Microsoft Product Support Services.