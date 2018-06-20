---
title: "Port Configuration Errors | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 92eae0d8-a0c4-4f8c-b91a-fd98b9f6931a
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Port Configuration Errors
Information for diagnosing and resolving WCF Port Configuration errors.  

## Cannot merge operation due to communication pattern conflict
  
|                 |                                                         Details                                                         |
|-----------------|-------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                    |
| Product Version |                               [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                |
|    Event ID     |                                                            0                                                            |
|  Event Source   |                                                            0                                                            |
|    Component    |                                                            0                                                            |
|  Symbolic Name  |                                                            0                                                            |
|  Message Text   | Cannot merge operation "{0}" due to communication pattern conflict.  All operations must be one-way or request-response |
  
### Explanation  
 This error indicates [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is attempting to merge ports with port types that have different communication patterns.  
  
### User Action  
 Using the Port Configuration Wizard, ensure that all the ports that are being merged have the same communication direction, either one-way or request-response.  
  
 For additional information on port configuration, see [How to Run the Port Configuration Wizard](../core/how-to-run-the-port-configuration-wizard.md).
 
## Port types that have a combination of one-way and request-response operations are not allowed 
  
|                 |                                                                                Details                                                                                |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                          [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                           |
| Product Version |                                                      [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                                       |
|    Event ID     |                                                                                   0                                                                                   |
|  Event Source   |                                                                                   0                                                                                   |
|    Component    |                                                                                   0                                                                                   |
|  Symbolic Name  |                                                                                   0                                                                                   |
|  Message Text   | Port types that have a combination of one-way and request-response operations are not allowed. Correct service description "{0}" port type "{1}" and rerun the wizard |
  
### Explanation  
 This error indicates the service trying to be consumed has operations that are both one-way and two-way (or request-response).  
  
### User Action  
 Correct the service with the appropriate operations (either one-way or request-response but not both) and try to consume (if you own the WCF services that you are trying to consume). Otherwise, contact the service provider.
