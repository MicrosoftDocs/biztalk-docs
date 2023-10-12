---
description: "Learn more about: Type cannot be found in namespace"
title: "Type cannot be found in namespace"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Type cannot be found in namespace
## Details  
  
| Field | Error Details |
|-----------------|------------------------------------------------------------------------------------|
|  Product Name   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| Product Version |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    Event ID     |                                         0                                          |
|  Event Source   |                                         0                                          |
|    Component    |                                         0                                          |
|  Symbolic Name  |                                         0                                          |
|  Message Text   |                Error: Type "{0}" cannot be found in namespace "{1}"                |
  
## Explanation  
 This error indicates artifacts that are created are referencing types which cannot be found in the namespace specified.  
  
## User Action  
 Add a reference that contain the type that is not found, and run the wizard again (if you own the WCF service that you are trying to consume). Otherwise, contact the service provider.
