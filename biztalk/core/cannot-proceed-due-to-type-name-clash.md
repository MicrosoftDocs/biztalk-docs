---
description: "Learn more about: Cannot proceed due to type name clash"
title: "Cannot proceed due to type name clash"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Cannot proceed due to type name clash
## Details  
  
|    Field    |                              Error Details                                                    |
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
