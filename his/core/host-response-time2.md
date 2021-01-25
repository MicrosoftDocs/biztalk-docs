---
description: "Learn more about: Host Response Time"
title: "Host Response Time2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4ffe30e8-4151-469c-87d2-d8c30d65b136
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Host Response Time
The host response time indicates the response time observed by the Transaction Integrator (TI) transport component, measuring the time from the call to the server computer, or TCP/IP stack, until the reply from the host. This includes some networking overhead. In a typical well-tuned high bandwidth LAN environment, this response time should be very close to the actual host processing time.  
  
 You should consider some important tuning issues, especially with SNA Link, in order to declare this to be the representative figure for the host. For more information, see [SNA Link Tuning](../core/sna-link-tuning1.md). For the host response time, TI again separates the CICS LINK mode, and the CICS non-LINK or IMS mode into two separate counters.  
  
## See Also  
 [Performance Monitoring Counters](../core/performance-monitoring-counters2.md)
