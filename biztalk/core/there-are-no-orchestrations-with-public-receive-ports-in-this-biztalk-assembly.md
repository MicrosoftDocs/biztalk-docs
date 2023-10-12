---
description: "Learn more about: There are no orchestrations with public receive ports in this BizTalk assembly"
title: "There are no orchestrations with public receive ports in this BizTalk assembly"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# There are no orchestrations with public receive ports in this BizTalk assembly
## Details  
  
| Field | Error Details |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                              [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                               |
| Product Version |                                                          [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                                           |
|    Event ID     |                                                                                       0                                                                                       |
|  Event Source   |                                                                                       0                                                                                       |
|    Component    |                                                                                       0                                                                                       |
|  Symbolic Name  |                                                                                       0                                                                                       |
|  Message Text   | There are no orchestrations with public receive ports in this BizTalk assembly. Click back and specify a BizTalk assembly containing orchestrations with public receive ports |
  
## Explanation  
 This error indicates the orchestration selected does not have a public port.  
  
## User Action  
 Use the following procedure to configure a public port.  
  
#### To configure a public port  
  
1.  Locate the orchestration and make the desired receive port public.  
  
    1.  Open the Port Configuration wizard.  
  
    2.  In **Select a Port Type**, change **Access Restrictions** from **Internal** (default) to **Public-no limits**.  
  
2.  Recompile the assembly.  
  
     \- OR -  
  
     Load a BizTalk assembly with public receive ports.
