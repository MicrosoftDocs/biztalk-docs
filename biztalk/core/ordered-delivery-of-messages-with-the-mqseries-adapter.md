---
description: "Learn more about: Ordered Delivery of Messages with the MQSeries Adapter"
title: "Ordered Delivery of Messages with the MQSeries Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "messages, ordered delivery"
  - "MQSeries adapters, ordered delivery"
ms.assetid: 517ff2a4-7315-43b5-8d4b-7494adf141e4
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Ordered Delivery of Messages with the MQSeries Adapter
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides an **Ordered Delivery** option for static send ports. Setting the **Ordered Delivery** option on a send port to **True** ensures that BizTalk Server delivers messages to the send port in the same order that they are published to the BizTalk MessageBox database. To provide end-to-end ordered delivery the following conditions must be met:  
  
-   Messages must be received with an adapter that preserves the order of the messages when submitting them to BizTalk Server. For example, when receiving messages with the MQSeries receive adapter, the receive location should be configured with the option **Order with Stop** or **Order with Suspend**.  
  
-   You must subscribe to these messages with a send port that has the **Ordered Delivery** option to **True**.  
  
-   If an orchestration is used to process the messages, only a single instance of the orchestration should be used, the orchestration should be configured to use a sequential convoy, and the **Ordered Delivery** property of the orchestration's receive port should be set to **True**.  
  
## Using the MQSeries Adapter for Ordered Delivery of Messages  
 The MQSeries receive adapter provides support for preserving the order of messages when submitting them to BizTalk Server. End-to-end ordered delivery of messages through BizTalk Server can be achieved when receiving messages with the MQSeries adapter if the messages are processed by a send port that is configured with the **Ordered Delivery** option set to **True**.  
  
## See Also  
 [Ordered Delivery of Messages](../core/ordered-delivery-of-messages.md)   
 [How to Configure MQSeries Adapter Receive Locations and Send Ports](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md)
