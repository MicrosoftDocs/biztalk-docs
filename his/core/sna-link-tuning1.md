---
title: "SNA Link Tuning1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a1eeb0c5-3fa5-4166-8d1a-3ffc21672ada
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# SNA Link Tuning
If you are using token-ring, Ethernet, or FDDI to communicate with your host system, investigate data link control (DLC) tuning. The following 802.2 connection default settings should be sufficient:  
  
- Unacknowledged Send limit is 8 by default.  
  
- Receive ACK threshold is 2 by default. However, some hosts are set to a Send Window of 1, so they require an ACK from [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] for every frame they send; whereas with the default of 2, the host can stop sending until the ACK has been received. The DLC will then go through the time-out and recovery, but the performance will be decreased significantly. It is important that you set each node's send window to be larger than its partner's receive window.  
  
- Maximum BTU length: 1929 for token-ring, 1493 for Ethernet. If a 16-Mbps token-ring is being used, and the TI request or host response will exceed this BTU length, increase the maximum BTU length to 4105 (or 8192 for the maximum possible) within the Host Integration Server connection.  
  
## Troubleshooting Suggestions  
 Capture a Network Monitor or Sniffer trace of [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] computer-to-host traffic, and provide it to an SNA support engineer. The engineer can use this trace to observe the Send Window and Receive ACK threshold being used by both ends by looking at the LLC traffic.  
  
## See Also  
 [SNA Communication Tuning](../core/sna-communication-tuning2.md)