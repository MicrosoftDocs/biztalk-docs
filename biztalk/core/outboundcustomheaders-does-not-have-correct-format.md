---
description: "Learn more about: OutboundCustomHeaders does not have correct format"
title: "OutboundCustomHeaders does not have correct format"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# OutboundCustomHeaders does not have correct format
## Details  
  
| Field | Error Details |
|-----------------|------------------------------------------------------------------------------------|
|  Product Name   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| Product Version |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    Event ID     |                                         0                                          |
|  Event Source   |                                         0                                          |
|    Component    |                                         0                                          |
|  Symbolic Name  |                                         0                                          |
|  Message Text   |                OutboundCustomHeaders does not have a correct format                |
  
## Explanation  
 The value of WCF.InboundHeaders or WCF.OutboundCustomHeaders  is not in the following format: \<headers\>….\</headers\>.  
  
## User Action  
 Wrap the property values with \<headers\> element.  
  
 For further information, see the following resource in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  
  
-   [Using SOAP Headers in WCF Messages with Pipeline Components](../core/using-soap-headers-in-wcf-messages-with-pipeline-components.md)
