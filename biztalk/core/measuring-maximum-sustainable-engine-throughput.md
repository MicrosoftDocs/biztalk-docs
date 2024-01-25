---
description: "Learn more about: Measuring Maximum Sustainable Engine Throughput"
title: "Measuring Maximum Sustainable Engine Throughput"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Measuring Maximum Sustainable Engine Throughput
One of the primary considerations when planning a BizTalk Server system should be to determine the maximum sustainable throughput (MST) of the system. The MST of a BizTalk Server system is measured as the highest load of message traffic that the BizTalk system can handle indefinitely in production. This is important because as load exceeds MST, messages are backlogged in the MessageBox database and message delivery may be delayed. If you calculate the MST of your BizTalk Server system as part of normal testing then you can scale your system to avoid extended overload scenarios in production.  
  
## In This Section  
  
-   [Factors that Affect Maximum Sustainable Performance](../core/factors-that-affect-maximum-sustainable-performance.md)  
  
-   [Test Scenarios for Measuring MST of the Engine](../core/test-scenarios-for-measuring-mst-of-the-engine.md)  
  
-   [Recommendations When Testing Engine Performance](../core/recommendations-when-testing-engine-performance.md)
