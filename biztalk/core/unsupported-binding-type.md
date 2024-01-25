---
description: "Learn more about: Unsupported binding type"
title: "Unsupported binding type"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Unsupported binding type
## Details  
  
|      Field      |                                  Error Details                                     |
|-----------------|------------------------------------------------------------------------------------|
|  Product Name   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| Product Version |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    Event ID     |                                         0                                          |
|  Event Source   |                                         0                                          |
|    Component    |                                         0                                          |
|  Symbolic Name  |                                         0                                          |
|  Message Text   |                              Unsupported binding type                              |
  
## Explanation  
 The MsmqIntegration binding was chosen, but is not supported by the WCF adapter.  
  
## User Action  
 Use the WCF-NetMsmq adapter. If native MSMQ messages need to be exchanged, use the BizTalk MSMQ adapter.  
  
 For further information on configuring adapters, see the following resource:  
  
-   [Configuring the WCF-NetMsmq Adapter](../core/configuring-the-wcf-netmsmq-adapter.md)
