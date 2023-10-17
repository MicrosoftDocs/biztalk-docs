---
description: "Learn more about: Unexpected root element"
title: "Unexpected root element"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Unexpected root element
## Details  
  
|      Field      |                                  Error Details                                     |
|-----------------|------------------------------------------------------------------------------------|
|  Product Name   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| Product Version |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    Event ID     |                                         0                                          |
|  Event Source   |                                         0                                          |
|    Component    |                                         0                                          |
|  Symbolic Name  |                                         0                                          |
|  Message Text   |                              Unexpected root element                               |
  
## Explanation  
 Header property is not in \<headers\>….\</headers\> format. This situation normally applies to InboundHeaders and OutboundCustomHeaders.  
  
## User Action  
 Ensure that header property is in the format of  \<headers\>…\</headers\>.
