---
title: "Escon Channel Throughput1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 55ed1c18-b6fa-4fc2-9601-a93bf828302c
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Escon Channel Throughput
Although the 100baseT LAN can operate with 3–5 MBps throughput range on a heavily loaded system, the Escon channel specified at 17 MBps can reach very close to its maximum specified throughput. Tests done with [!INCLUDE[hisHostIntServNoVersion](../core/includes/hishostintservnoversion-md.md)] on a channel-attached quad PP200 were able to reach 12 MBps against a large mainframe using LU 6.2 doing straight memory-to-memory transfer. This rate is not typically reached except during system backup procedures or database distribution.  
  
 To place this result in the right context for a large online transaction processing (OLTP) system doing 500 TPS with transactions typically consisting of 200-byte input and 1900-byte reply, the Escon overall data rate would be 1 MBps plus some overhead. The Escon channel rarely becomes the system bottleneck because one adapter can support multiple 17-MBps channels using the Escon Multiple Image Facility (EMIF).  
  
## See Also  
 [System Sizing](../core/system-sizing.md)