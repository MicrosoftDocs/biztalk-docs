---
title: "What Is the Adapter Framework? | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bd1e2fd7-4e77-49c4-839d-c2bf16b10ba2
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# What Is the Adapter Framework?
The BizTalk Adapter Framework offers a stable, open mechanism for all adapters to implement or access work from the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Messaging Engine. The interfaces described in the **Microsoft.BizTalk.Adapter.Framework** namespace enable adapters to provide a means to modify configuration property pages. It also is a means to import services and schemas into the BizTalk project.  
  
 The following figure shows how an adapter and the Adapter Framework work together to connect your application to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 ![The adapter framework](../core/media/ebiz-sdk-adpttoday.gif "ebiz_sdk_adpttoday")  
  
 The following steps describe the sequence of steps shown in this figure:  
  
1. Data is received from a receive location that is listening for messages with a certain protocol at a specified address. The receive location is associated with an adapter and a receive pipeline. You can configure both the adapter and the pipeline components to perform certain logic on messages of a predetermined protocol.  
  
2. After the message is received by the receive location, the message is sent to the adapter, which creates a new BizTalk message, attaches the data stream to the message (typically in the body part of the message), adds any metadata pertaining to the endpoint over which the data was received, and then submits that message into the Messaging Engine.  
  
3. The Messaging Engine sends the message to the receive pipeline where the data is transformed into XML, the message sender is authenticated, the message is decrypted, and the XML is validated.  
  
4. The Messaging Engine publishes the message to the MessageBox database. The MessageBox is a Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] table containing messages to be processed. Both orchestrations and send ports can subscribe to the MessageBox.  
  
5. The Messaging Engine sends the message to either an orchestration or a send port subscriber based upon the message context properties matching the specifications set in the filter on the subscriber.  
  
6. If an orchestration is the subscriber, it processes the message and sends it out through a send port. If the subscriber is a send the message passes through the send pipeline into a send adapter before being transmitted.  
  
## In This Section  
  
-   [Using the Adapter Framework Tools](../core/using-the-adapter-framework-tools.md)  
  
-   [Adapter Message Exchange Patterns](../core/adapter-message-exchange-patterns.md)  
  
-   [Adapter Framework Components](../core/adapter-framework-components.md)  
  
-   [Adapter Hosting Model](../core/adapter-hosting-model.md)  
  
-   [Adapter Components](../core/adapter-components.md)