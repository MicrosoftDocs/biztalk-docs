---
title: "MQSC Adapter Features | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b2c43fab-5da3-4e81-ae14-5091649f6d83
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# MQSC Adapter Features

## Overview
The Client-Based BizTalk Adapter for WebSphere MQ (MQSC Adapter) is designed for BizTalk Server and works with all the BizTalk Server components and tools. With the adapter, you can do the following:  
  
- Communicate with remote Queue Managers that are running on Windows or other operating systems directly from BizTalk Server.  
  
- Send messages to MQSeries Remote Queue Definitions, Local queues, Transmission queues, and Alias queues from BizTalk Server.  
  
- Receive messages from MQSeries Transmission queues, Local queues, and Alias queues.  
  
- Support clustered MQSeries Queue Managers.  
  
- Support clustered BizTalk servers.  
  
- Poll MQSeries Queues with wait interval.  
  
- Configure Static, Dynamic, Solicit-Response send ports, and Static Receive Locations for this adapter.  
  
- Map context properties to header properties for both transmitting and receiving messages. Gain easy programmatic access to MQSeries header properties (including MQMD, MQXQH, MQCIH, and MQIIH) through BizTalk context properties.  
  
- Receive messages in batches from MQSeries queues.  
  
  The MQSC Adapter also does the following:  
  
- Enables correlation with either BizTalk Server or MQSeries using the correlation identifier.  
  
- Provides ordered delivery of messages.  
  
- Provides Secure Sockets Layer (SSL) support for secure communication with remote MQSeries Queue Managers.  
  
  The MQSC Adapter can co-exist with the Server-Based Microsoft BizTalk Adapter for WebSphere MQ (MQSeries Adapter).  
  
## See Also  
 [BizTalk Adapter for WebSphere MQ](../core/biztalk-adapter-for-websphere-mq2.md)   