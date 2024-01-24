---
description: "Learn more about: Unable to import client endpoint configuration"
title: "Unable to import client endpoint configuration"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Unable to import client endpoint configuration
## Details  
  
|      Field      |                                  Error Details                                     |
|-----------------|------------------------------------------------------------------------------------|
|  Product Name   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| Product Version |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    Event ID     |                                         0                                          |
|  Event Source   |                                         0                                          |
|    Component    |                                         0                                          |
|  Symbolic Name  |                                         0                                          |
|  Message Text   |                   Unable to import client endpoint configuration                   |
  
## Explanation  
 There could be more than one explanation for this error. The configuration file may contain invalid characters. The root element may be missing. The data at the root level may be invalid.  
  
## User Action  
 Verify the validity of the configuration file. Try to open the configuration file with the Service Configuration Editor (**svcConfigEditor.exe**) and verify each property.
