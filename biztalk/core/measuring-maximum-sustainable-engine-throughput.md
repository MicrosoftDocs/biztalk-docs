---
description: "Learn more about: Measuring Maximum Sustainable Engine Throughput"
title: "Measuring Maximum Sustainable Engine Throughput | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "maximum sustainable throughput (MST)"
  - "maximum sustainable throughput (MST), about maximum sustainable throughput (MST)"
  - "performance, maximum sustainable thoughput (MST)"
ms.assetid: d83f734f-1a44-4da0-a755-45ba204cadaf
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Measuring Maximum Sustainable Engine Throughput
One of the primary considerations when planning a BizTalk Server system should be to determine the maximum sustainable throughput (MST) of the system. The MST of a BizTalk Server system is measured as the highest load of message traffic that the BizTalk system can handle indefinitely in production. This is important because as load exceeds MST, messages are backlogged in the MessageBox database and message delivery may be delayed. If you calculate the MST of your BizTalk Server system as part of normal testing then you can scale your system to avoid extended overload scenarios in production.  
  
## In This Section  
  
-   [Factors that Affect Maximum Sustainable Performance](../core/factors-that-affect-maximum-sustainable-performance.md)  
  
-   [Test Scenarios for Measuring MST of the Engine](../core/test-scenarios-for-measuring-mst-of-the-engine.md)  
  
-   [Recommendations When Testing Engine Performance](../core/recommendations-when-testing-engine-performance.md)
