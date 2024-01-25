---
description: "Learn more about: Cannot merge operations due to name collision"
title: "Cannot merge operations due to name collision"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Cannot merge operations due to name collision
## Details  
  
|    Field    |                                         Error Details                                                               |
|-----------------|-------------------------------------------------------------------------------------------------------------|
|  Product Name   |             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]              |
| Product Version |                         [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                          |
|    Event ID     |                                                      0                                                      |
|  Event Source   |                                                      0                                                      |
|    Component    |                                                      0                                                      |
|  Symbolic Name  |                                                      0                                                      |
|  Message Text   | Cannot merge operation "{0}" due to name collision. All operations in a web service must have unique names. |
  
## Explanation  
 This error indicates the port name or the operation name of two different ports that are being merged have the same name.  
  
## User Action  
 Using the Port Configuration Wizard, ensure that all the ports that are being merged have different port names and operation.  
  
 For additional information on port configuration, see the following resource in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  
  
-   [How to Run the Port Configuration Wizard](../core/how-to-run-the-port-configuration-wizard.md)
