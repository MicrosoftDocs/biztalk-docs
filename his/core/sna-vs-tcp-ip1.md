---
description: "Learn more about: SNA vs. TCP/IP"
title: "SNA vs. TCP-IP1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# SNA vs. TCP/IP
TCP/IP is not as scalable as SNA with Transaction Integrator (TI), but TCP/IP is more effective in other areas such as file transfer and data access (about 10-15% better on OLEDB tests). In addition, the IBM endorsement of TCP/IP simplifies the corporate networking infrastructure and enables easier interoperability to the Internet.  
  
 To study the performance differences for TI with TCP/IP as the up-stream link protocol versus SNA, Microsoft performed a stress test where the only change to the setup was the up-link protocol. The SNA test was set to use the `SelectionHint` property setting because this is the same process performed by the TCP/IP up-link. For more information about the effects of the `SelectionHint` property, see [Remote Environment Selection with the SelectionHint Property](../core/remote-environment-selection-with-the-selectionhint-property2.md).  
  
 Analyzing the average response time as a function of transactions performed, Microsoft found that TCP/IP is as fast as SNA. In fact, TCP/IP is faster than SNA when the load is below 100 transactions per second (tps). For some deployments, that is the typical operating range. As the load increases, the connectionless TCP/IP up-link starts to slow down the response time and clips the top performance at 500 tps. The SNA up-link enables stable response times throughout the load range, and therefore achieves higher scalability.  
  
 To analyze the superior scalability of SNA compared to TCP/IP, Microsoft charted the frames per second over the backbone LAN. Whereas SNA maintains its sessions from transaction to transaction, TCP/IP must establish and destroy the TCP/IP connection for each transaction. This results in more frames transmitted over the up-link compared to SNA. In our tests, the 100baseT Ethernet LAN did not become a bottleneck, but this can become the critical issue if the link speed between the TI server and the host is slower. In any case, the TCP/IP connections and disconnections generate some additional interrupts for both ends.  
  
 Additional analysis shows an advantage that the TCP/IP up-link has over the SNA up-link that might become the deciding factor in a real-world deployment. When you are using the SNA up-link, the TI Automation server must endure almost twice the amount of context switching compared to the TCP/IP up-link case. This is because with SNA, the messages are passed from TI first to the SNA server node and then to the SNA link service. These are separate processes, so there is process-to-process communication and context switching. With TCP/IP this does not occur; TI passes the messages directly to the NDIS driver. On a server where additional processing of business logic is occurring, so much context switching may occur that throughput and scalability are affected.  
  
## See Also  
 [Transaction Integrator Performance Guide](../core/transaction-integrator-performance-guide1.md)
