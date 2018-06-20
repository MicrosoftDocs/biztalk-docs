---
title: "Cannot obtain scheme from binding to validate address | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b002084a-63ae-4685-8ce3-88cc6489e19e
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Cannot obtain scheme from binding to validate address
## Details  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  Product Name   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| Product Version |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    Event ID     |                                         0                                          |
|  Event Source   |                                         0                                          |
|    Component    |                                         0                                          |
|  Symbolic Name  |                                         0                                          |
|  Message Text   |               Cannot obtain scheme from binding to validate address.               |
  
## Explanation  
 The transport binding element that has been specified does not have a scheme.  
  
## User Action  
 Make sure that the transport binding element has a valid scheme, or that a valid transport binding element is selected. If using a custom binding, make sure a valid transport binding element is specified.  
  
 For additional information, see the following resources in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  
  
-   [Configuring the WCF-Custom Adapter](../core/configuring-the-wcf-custom-adapter.md)