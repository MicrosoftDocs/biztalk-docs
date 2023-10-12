---
description: "Learn more about: Message types without parts are not supported"
title: "Message types without parts are not supported"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Message types without parts are not supported
## Details  
  
| Field | Error Details|
|-----------------|---------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                     |
| Product Version |                                [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                 |
|    Event ID     |                                                             0                                                             |
|  Event Source   |                                                             0                                                             |
|    Component    |                                                             0                                                             |
|  Symbolic Name  |                                                             0                                                             |
|  Message Text   | Message types without parts are not supported. Correct service description "{0}" message type "{1}" and rerun the wizard. |
  
## Explanation  
 This error indicates the service that is trying to be consumed does not have a message type defined.  
  
## User Action  
 Correct the service with the appropriate message type and try to consume (if you own the WCF services that you are trying to consume). Otherwise, contact the serviced provider.  For additional information on messages, see the following resource in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Help:  
  
-   [Constructing Web Messages](../core/constructing-web-messages.md)
