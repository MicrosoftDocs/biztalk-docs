---
title: "Message part missing element | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b519315f-d51d-4ca3-a0e6-d08bb920c6c5
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message part missing element
## Details  
  
|                 |                                                                                                                    |
|-----------------|--------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                 |
| Product Version |                             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                             |
|    Event ID     |                                                         0                                                          |
|  Event Source   |                                                         0                                                          |
|    Component    |                                                         0                                                          |
|  Symbolic Name  |                                                         0                                                          |
|  Message Text   | Message part missing element. Correct service description "{0}" message type "{1}" part "{2}" and rerun the wizard |
  
## Explanation  
 This error indicates the service that is trying to be consumed does not have the element tag identifying the type of message.  
  
## User Action  
 Correct the service with the appropriate message type and try to consume (if you own the WCF services that you are trying to consume). Otherwise, contact the service provider.  
  
 For additional information on messages, see the following resource in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  
  
-   [Constructing Web Messages](../core/constructing-web-messages.md)