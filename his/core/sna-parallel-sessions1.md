---
description: "Learn more about: SNA Parallel Sessions"
title: "SNA Parallel Sessions1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b038f6f4-0703-491d-b1a8-0117d5da7b02
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# SNA Parallel Sessions
Each active transaction allocates one parallel session to interact with the host when SNA is used instead of TCP/IP. This session is activated when the transaction sends the attach message (allocate conversation) and released after the forget message (TpEnded). When you configure too few parallel sessions for the SNA connection, the transactions that are waiting for the active ones to release can start queuing up. To avoid this queuing problem, configure enough sessions for the worst-case scenario.  
  
> [!NOTE]
>  SNA Server 4.0 SP3 required the use of a contention winner session, but [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] does not. Host Integration Server can use any session as it becomes available.  
  
 Host Integration Server can handle large numbers of parallel sessions. The maximum is 30,000 parallel sessions for each LU-LU pair, after which another LU-LU pair must be configured. The CICS system is a bit more sensitive to the amount of parallel sessions configured. Contact your CICS systems experts for the appropriate session count.  
  
## See Also  
 [Transaction Programs that Run for a Long Time](../core/transaction-programs-that-run-for-a-long-time2.md)
