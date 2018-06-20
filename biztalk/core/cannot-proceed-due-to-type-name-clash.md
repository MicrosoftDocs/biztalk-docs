---
title: "Cannot proceed due to type name clash | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2ced6de4-0950-498e-a548-5c85419726d8
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Cannot proceed due to type name clash
## Details  
  
|                 |                                                                                       |
|-----------------|---------------------------------------------------------------------------------------|
|  Product Name   |  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |              [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]               |
|    Event ID     |                                           0                                           |
|  Event Source   |                                           0                                           |
|    Component    |                                           0                                           |
|  Symbolic Name  |                                           0                                           |
|  Message Text   | Cannot proceed due to type name clash. The name "{0}" already exists in the namespace |
  
## Explanation  
 This error indicates multiple artifacts in the same defined namespace have the same name.  
  
## User Action  
 Rename the artifacts in the same namespace or put them in a different namespace.