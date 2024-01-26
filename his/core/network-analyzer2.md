---
description: "Learn more about: Network Analyzer"
title: "Network Analyzer2"
ms.custom: ""
ms.date: "01/26/2024"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Network Analyzer
A network analyzer, is an important tool for checking the load and throughput on the network as well as verifying that there are no mismatched configurations in the test environment.  
  
You can use a network analyzer to confirm the transaction counts by monitoring the IP-DLC traffic to and from the computer being tested. You can filter traffic to count only incoming I-frames of a certain size and type. Using filtering, you can determine the number of accepted frames and ascertain the number of responses from the receiver servers.
  
 Another important measurement that uses a network analyzer is following the network bandwidth usage. Ethernet, in particular, slows down drastically when usage rates grow beyond 40–50 percent. Finally, the network analyzer can be used to confirm proper tuning of local area network (LAN) protocols.  

 A typical time for message transmission in [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] is between 1–5 milliseconds, even on almost full CPU loads. A transmission time longer than 1–5 milliseconds indicates a configuration mismatch or lack of available RAM because the system is using the virtual memory on the hard drive.
  
## See Also  
 [Status and Performance Information](../core/status-and-performance-information1.md)
