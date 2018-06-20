---
title: "Invalid scheme | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3bb3e70a-d23c-45e9-bde5-edae6731e58a
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Invalid scheme
## Details  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  Product Name   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| Product Version |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    Event ID     |                                         0                                          |
|  Event Source   |                                         0                                          |
|    Component    |                                         0                                          |
|  Symbolic Name  |                                         0                                          |
|  Message Text   |                  Invalid scheme; expecting scheme "{0}" or "{1}"                   |
  
## Explanation  
 One of the following situations has occurred: the address that is specified in the URI (uniform resource identifier) field must start with either http:// or https://. Or the scheme does not match what is specified in the implementation of the transport binding element.  
  
## User Action  
 Enter a valid proxy address URI that starts with http:// or https://