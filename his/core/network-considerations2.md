---
title: "Network Considerations2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9ca1a1f9-fac2-4455-ab0d-521afa91af0e
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Network Considerations
Your network adapter can have a large impact on the overall network performance. Advanced adapters provide good setup options to optimize the network I/O performance. Look for I/O buffering on the card itself, direct memory access (DMA) (adjustable data link control (DLC) (maximum frame size, and local area network (LAN) speed setting parameters.  
  
 [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] performance tuning involves adjusting the frame size, BTU size, and DLC-level pacing on the connection properties, as well as the request/response unit (RU) size and session-level pacing on the mode properties.  
  
 Additional tips:  
  
-   Your test data buffer must fit into one RU; if the RU size is too large, it will consume excess memory. 1200 bytes of screen paint data fits into an RU of 1484 bytes. This is the optimum for Ethernet. A 1920-byte data buffer would require two client/server message frames.  
  
-   The maximum BTU size needs to be at least the RU size + 9 bytes. For Ethernet, an RU of 1484 bytes and a BTU of 1493 bytes is good. For TokenRring, an RU of 4087 bytes and a BTU of 4096 bytes is a good starting point.  
  
-   The DLC level pacing is the most common tuning problem. To avoid deadlocks and timeouts, set the pacing between the two nodes so that the receiving window is one frame smaller than the partners send window. For example, node A can be set to send seven frames until it stops and waits for acknowledgement from node B; node B can be set to send an ACK after it receives six frames from node A, and vice versa. This guarantees successful DLC frame acknowledgements between the nodes.  
  
-   Setting the DLC receive acknowledgement to 1 or 2 would cause a receive ready (RR) to be sent after every second I-frame. This results in unnecessary control frame overhead on the LAN between the gateway and the server.  
  
## See Also  
 [Performance Tuning](../core/performance-tuning2.md)   
 [Status and Performance Information](../core/status-and-performance-information1.md)