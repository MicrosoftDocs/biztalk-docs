---
description: "Learn more about: Invalid identifier"
title: "Invalid identifier"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Invalid identifier
## Details  
  
| Field | Error Details |
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
