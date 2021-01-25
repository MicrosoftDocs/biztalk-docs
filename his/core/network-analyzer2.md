---
description: "Learn more about: Network Analyzer"
title: "Network Analyzer2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: af37fec2-f49e-4c52-a2e9-0b00b4dd854b
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Network Analyzer
A network analyzer, is an important tool for checking the load and throughput on the network as well as verifying that there are no mismatched configurations in the test environment.  
  
 You can use a network analyzer to verify the transaction counts by monitoring the data link control (DLC) traffic to and from the computer being tested. You can filter traffic to count only incoming I-frames of a certain size and type. Using filtering, you can determine the number of accepted frames and ascertain the number of responses from the receiver servers.  
  
 Another important measurement that uses a network analyzer is following the network bandwidth usage. Ethernet, in particular, slows down drastically when usage rates grow beyond 40–50 percent. A Token Ring network is more predictable in throughput even on higher loads; however, going beyond 60 percent network load levels should be cause for attention. Finally, the network analyzer can be used to confirm proper tuning of local area network (LAN) protocols. DLC level pacing (send and receive window size), timeouts, and retransmissions could artificially limit LAN throughput, perhaps to the point that the LAN, rather than the system under test, is the performance-limiting component.  
  
 Looking at the captured messages will give a good indication of problems and where they are. If there are Receiver Not Ready (RNR) frames present, one of the nodes is overloading and then limiting the message flow in. You can minimize an excess number of Receiver Ready (RR) messages by adjusting the DLC level pacing for a larger send and receive window. Long elapsed times between the individual frames can highlight configuration problems. This indicates which of the components, client, gateway, or server, consume most of the processing time. A single client test is a good way to determine where the delays might be.  
  
 A typical time for message transmission in [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] is between 1–5 milliseconds, even on almost full CPU loads. A transmission time longer than 1–5 milliseconds indicates a configuration mismatch or lack of available RAM because the system is using the virtual memory on the hard drive.  
  
## See Also  
 [Status and Performance Information](../core/status-and-performance-information1.md)
