---
description: "Learn more about: Registry Errors"
title: "Registry Errors"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Registry Errors
Information for diagnosing and resolving WCF Registry errors.  

## Failed to access the registry
  
| Field | Error Details |
|-----------------|------------------------------------------------------------------------------------|
|  Product Name   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| Product Version |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    Event ID     |                                         0                                          |
|  Event Source   |                                         0                                          |
|    Component    |                                         0                                          |
|  Symbolic Name  |                                         0                                          |
|  Message Text   |                             Failed to open HKLM\\{0}.                              |
  
### Explanation  
 This error indicates a failure to access the registry.  
  
### User Action  
 Ensure you have read access to the registry. To access the registry, ensure you have Administrator privileges or contact the administrator of the machine.
 
## Failed to obtain BizTalk install path
  
| Field | Error Details |
|-----------------|------------------------------------------------------------------------------------|
|  Product Name   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| Product Version |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    Event ID     |                                         0                                          |
|  Event Source   |                                         0                                          |
|    Component    |                                         0                                          |
|  Symbolic Name  |                                         0                                          |
|  Message Text   |             Failed to obtain BizTalk install path from HKLM\\{0}\\{1}              |
  
## Explanation  
 This error indicates a failure to access the registry, and that the key has an incorrect value.  
  
## User Action  
 Ensure you have read access to the registry. Ensure the key has the correct value. To access the registry, ensure you have Administrator privileges or contact the administrator of the machine. 
