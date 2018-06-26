---
title: "Cannot create standard metadata binding for scheme | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ce441c3e-0f6e-46ed-90cf-825dbf89d910
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Cannot create standard metadata binding for scheme
## Details  
  
|                 |                                                                                                                    |
|-----------------|--------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                 |
| Product Version |                             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                             |
|    Event ID     |                                                         0                                                          |
|  Event Source   |                                                         0                                                          |
|    Component    |                                                         0                                                          |
|  Symbolic Name  |                                                         0                                                          |
|  Message Text   | Cannot create standard metadata binding for scheme "{0}". Supported schemes are http, https, net.pipe, and net.tcp |
  
## Explanation  
 This error indicates the service from which the metadata is trying to be consumed is not a supported scheme.  
  
## User Action  
 Publish the metadata with a valid scheme and then run the wizard again, against the new metadata location.  
  
 For additional information on adapters and binding, see the following resources in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  
  
-   [WCF Adapters](../core/wcf-adapters.md)