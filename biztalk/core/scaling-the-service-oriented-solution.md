---
title: "Scaling the Service Oriented Solution | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "scaling, service solutions"
  - "service solution tutorial, scaling"
ms.assetid: 6c22a68d-03e7-4174-b612-0e2246aa9413
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Scaling the Service Oriented Solution
To scale the solution to support higher throughput while maintaining low message latency requires you to use the inline version of the solution. The inline solution bypasses the MessageBox database when interacting with the back-end systems.  
  
 You can also add BizTalk Server processing servers to run orchestrations. This decreases the utilization of each server so that new requests can be processed quickly. You can also scale up the MessageBox server so that it has enough additional capacity to handle the message throughput.  
  
 However, the service oriented architecture solution does not benefit from having multiple MessageBox databases. Multiple MessageBoxes require distributed transaction coordinator (DTC) transactions. The transactions increase overall message latency.  
  
 You can decrease response time by eliminating the pipeline component that adds MQSeries header information. For more information, see [Implementation Highlights of the Service Oriented Solution](../core/implementation-highlights-of-the-service-oriented-solution.md).  
  
## See Also  
 [Developing a Service Oriented Solution](../core/developing-a-service-oriented-solution.md)