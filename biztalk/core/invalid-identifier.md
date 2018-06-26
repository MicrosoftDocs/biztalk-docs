---
title: "Invalid identifier | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f87e1e42-457f-4d04-a1d2-6b796f3fa7b7
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Invalid identifier
## Details  
  
|                 |                                                                                                                                                                           |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                            [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                             |
| Product Version |                                                        [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                                         |
|    Event ID     |                                                                                     0                                                                                     |
|  Event Source   |                                                                                     0                                                                                     |
|    Component    |                                                                                     0                                                                                     |
|  Symbolic Name  |                                                                                     0                                                                                     |
|  Message Text   | "{0}" is not a valid identifier. Restoring original name. (A valid identifier consists of a letter followed by zero or more letters or digits and cannot contain spaces.) |
  
## Explanation  
 This error indicates the web methods defined when publishing a schema is not a valid .net identifier.  
  
## User Action  
 Rename the web methods to a valid .net identifier. A valid identifier consists of a letter followed by zero or more letters or digits and cannot contain spaces.