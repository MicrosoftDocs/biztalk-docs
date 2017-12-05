---
title: "Host (VTAM, CICS or IMS) Response Time2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e03c7e14-fa77-4e51-aea8-474388835084
caps.latest.revision: 3
---
# Host (VTAM, CICS or IMS) Response Time
The host response time, also called the unit of work (UOW) or host processing time, for each transaction affects the number of transactions that can be performed given the number of LU 6.2 sessions that are used.  
  
 If CICS is used, investigate the CICS region definitions for parallel session limit and contention winner limit. These values are configured in the Maximum parameter in the CICS region SESSION PROPERTIES:  
  
 SESSION PROPERTIES Maximum==>100, 000  
  
 The first value is the parallel session limit and the second value is the CICS contention winner limit. For Transaction Integrator (TI) use, Host Integration Server should be configured as the contention winner for all sessions, so you should set the CICS contention winner limit to zero (0). Also, verify that the CICS region maximum tasks value is sufficient to handle the concurrent client requests.  
  
 If you are using IMS, verify that IMS has sufficient message processing regions to handle the expected load.  
  
## Troubleshooting Suggestions  
 Capture a [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] data link control (DLC) message trace of the throughput test and analyze the host response time observed on the LU 6.2 sessions.  
  
 Within a Host Integration Server DLC message trace, a unique LU 6.2 session is distinguished by a unique Originating Address Field (OAF), Destination Address Field (DAF), and OAF/DAF Assignor Indicator (ODAI) values. The OAF and DAF specified in a Host Integration Server session request will alternate on the host response.  
  
> [!NOTE]
>  Either end can deallocate the conversation, although this is often done by TI. However, it is possible for the host data response to contain the Conditional End Bracket (CEB).  
  
## See Also  
 [SNA Communication Tuning](../core/sna-communication-tuning1.md)