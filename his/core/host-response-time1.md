---
title: "Host Response Time1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9b578694-7ea3-473d-aa5f-8cc3ebc5546a
caps.latest.revision: 3
---
# Host Response Time
The host response time indicates the response time observed by the Transaction Integrator (TI) transport component, measuring the time from the call to the server computer, or TCP/IP stack, until the reply from the host. This includes some networking overhead. In a typical well-tuned high bandwidth LAN environment, this response time should be very close to the actual host processing time.  
  
 You should consider some important tuning issues, especially with SNA Link, in order to declare this to be the representative figure for the host. For more information, see [SNA Link Tuning](../core/sna-link-tuning2.md). For the host response time, TI again separates the CICS LINK mode, and the CICS non-LINK or IMS mode into two separate counters.  
  
## See Also  
 [Performance Monitoring Counters](../core/performance-monitoring-counters1.md)