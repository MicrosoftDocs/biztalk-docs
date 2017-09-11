---
title: "Character Encoding | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "transaction support"
  - "character encoding"
  - "encoding characters"
  - "messages, character encoding"
ms.assetid: 0a0c21c8-3318-4533-9734-89302527cb67
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Character Encoding
TIBCO Enterprise Message Service (EMS) supports different character encoding in the messages transmitted to EMS by BizTalk Adapter for TIBCO EMS. Messages are encoded using the default UTF-8 encoding. When receiving messages, the adapter determines the encoding of the message and converts the appropriate strings to UTF-8 before providing the message to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. All character conversions use the Microsoft .NET Framework classes; therefore the adapter supports the character conversions provided by this same framework.  
  
## Running in a Clustered Environment  
 Messages published to queues are consumed by the consumers in an order pre-determined by the EMS server—only one adapter in the clustered [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment receives the message. The queue can be configured as *exclusive*. This means that only the first adapter that registers itself for message consumption on the queue receives the messages. The EMS server only sends messages to the other consumers if the exclusive consumer does not acknowledge message reception. Exclusive queue configuration is performed in the EMS configuration and is not client configurable.  
  
> [!NOTE]
>  Regarding subscriptions to topics: because all adapters in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group are configured identically, they are all subscribed for the message, and each topic subscription receives the message.  
  
## Transaction Support  
 The adapter provides support for transactions when required by the orchestration send ports. There is no transaction support with the EMS server when the adapter is listening for messages; however, the adapter acknowledges reception of all messages from EMS after successful message submission to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. EMS resends unacknowledged messages to the adapter.  
  
## See Also  
 [Security in BizTalk Adapter for TIBCO EMS](../core/security-in-biztalk-adapter-for-tibco-ems.md)   
 [Getting Started](../core/getting-started-with-biztalk-adapter-for-tibco-enterprise-message-service.md)