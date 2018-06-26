---
title: "Communication Pattern Errors | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 06656073-9bae-4d6f-98ae-2714a72ee79c
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Communication Pattern Errors
Information for diagnosing and resolving WCF Communication Pattern errors.  

## Fault messages are not supported on one-way ports
  
|                 |                                                       Error details                                                       |
|-----------------|---------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                     |
| Product Version |                                [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                 |
|    Event ID     |                                                             0                                                             |
|  Event Source   |                                                             0                                                             |
|    Component    |                                                             0                                                             |
|  Symbolic Name  |                                                             0                                                             |
|  Message Text   | Fault messages are not supported on one-way ports. Correct service description "{0}" port type "{1}" and rerun the wizard |
  
## Explanation  
 This error indicates the service trying to be consumed is a one-way service and has the fault specified.  
  
## User Action  
 Correct the service by switching the communication pattern from one-way to request-response. Or remove the fault in the code.
 
 