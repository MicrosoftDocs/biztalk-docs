---
description: "Learn more about: Communication Pattern Errors"
title: "Communication Pattern Errors"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Communication Pattern Errors
Information for diagnosing and resolving WCF Communication Pattern errors.  

## Fault messages are not supported on one-way ports
  
|      Field      |                                                       Error details                                                       |
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
 
 
