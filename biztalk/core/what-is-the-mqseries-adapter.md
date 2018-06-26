---
title: "What Is the MQSeries Adapter? | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MQSeries adapters, about MQSeries adapters"
  - "MQSeries adapters"
ms.assetid: fd3dfa9a-344a-46e5-a342-bc56da7c1c50
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# What Is the MQSeries Adapter?
With the MQSeries adapter you can send and receive messages to MQSeries systems using Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 The adapter relies on MQSeries Server for Windows. This design guarantees reliable messaging because MQSeries Server for Windows supports Microsoft Distributed Transaction Coordinator (MSDTC).  
  
 The adapter supports clustered MQSeries Servers and clustered MQSeries Queue Managers, and also clustered BizTalk servers.  
  
 You can do the following with the MQSeries adapter:  
  
- Send messages to MQSeries remote definition queues, local queues, transmission queues, and alias queues from BizTalk Server.  
  
- Receive messages from MQSeries transmission queues, local queues, and alias queues.  
  
- Send and receive messages from MQSeries Server for Windows (MQSeries Server can run on the same computer as BizTalk Server or on a remote installation). You only have to deploy one copy of MQSAgent (the COM+ component of the adapter) to support all your BizTalk Server installations.  
  
- Poll MQSeries Server with a wait interval.  
  
- Use dynamic send ports to control the adapter.  
  
- Dynamically create queues at run time.  
  
- Dynamically receive messages from queues based upon MQSeries MatchOptions.  
  
- Map context properties to header properties for both transmitting and receiving messages. You can get and set MQSeries header properties (including MQMD, MQXQH, MQCIH, and MQIIH) through BizTalk Server context properties.  
  
- Enable correlation with either [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] or MQSeries Server creating the correlation identifier.  
  
- Request transactional and nontransactional delivery of messages for send and receive.  
  
> [!NOTE]
>  When using features such as MQSeries which make Distributed Component Object Model (DCOM) calls to the server, make sure you do not have a Network Address Translation (NAT)-based firewall enabled. The client must be able to access the server by its actual IP address, and NAT-based firewalls translate this address to something the client will not recognize.  
  
## In This Section  
  
-   [Components of the MQSeries Adapter](../core/components-of-the-mqseries-adapter.md)  
  
-   [MQSeries Adapter Architecture](../core/mqseries-adapter-architecture.md)  
  
-   [Using the MQSeries Adapter](../core/using-the-mqseries-adapter.md)  
  
-   [MQSeries Adapter Security](../core/mqseries-adapter-security.md)