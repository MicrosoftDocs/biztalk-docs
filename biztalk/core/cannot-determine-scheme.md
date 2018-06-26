---
title: "Cannot determine scheme | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2cc6e50b-33f5-4a88-b35d-075fdf8d79b2
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Cannot determine scheme
## Details  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  Product Name   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| Product Version |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    Event ID     |                                         0                                          |
|  Event Source   |                                         0                                          |
|    Component    |                                         0                                          |
|  Symbolic Name  |                                         0                                          |
|  Message Text   |                 Cannot determine scheme; specify a valid binding.                  |
  
## Explanation  
 The transport binding element that has been specified does not have a scheme.  
  
## User Action  
 Select a valid binding and make sure the transport binding element has a valid scheme. If using a custom binding, make sure a valid transport binding element is specified.  
  
 For additional information, see the following resources in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  
  
-   [Configuring the WCF-Custom Adapter](../core/configuring-the-wcf-custom-adapter.md)