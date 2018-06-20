---
title: "Other Activities That Can Affect Dehydration Behavior | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ed940448-d3b1-4308-9b38-887904e03bd0
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Other Activities That Can Affect Dehydration Behavior
The following activities directly or indirectly impact dehydration and overall performance and so should be factored into any testing scenarios.  
  
- **BizTalk Server Administration Console queries.** These queries consume resources and affect overall throughput depending on the type and frequency of the query.  
  
- **Backup, archiving, and purging activities.** These activities also consume resources and should be factored into any testing scenarios.  
  
- **Mixed 32-bit and 64-bit hosts.** Here are some things to consider when using mixed 32-bit and 64-bit hosts:  
  
  - Under stress we measure consumed virtual and physical memory and compare that against certain thresholds. In 64 bit systems the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] process uses more memory so there will be a difference in dehydration policy from 32-bits using the same system and the same default values. Be sure to separate orchestration, receive, send and message box hosts.  
  
     There is not an obvious difference when using the default 32-bit thresholds for 64-bit systems, as long as only the orchestration host is on the 64 bit box. However, under stress the various **MemoryThrottlingCriteria** settings should be at least doubled or tripled (as long as you have enough memory), but the scenario should be tuned for maximizing throughput because there are many factors that come into play. You should tune the dehydration thresholds under stress to find what is optimal for them.  
  
  - Dehydration behavior depends on delivery time history of every subscription; the histories could be different for different subscriptions so consider this in tuning your dehydration property values.  
  
  - When the orchestration host service is recycled on one host, but not on another, the histories will be different.  
  
  - When servers are using different versions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], there will be a difference in dehydration policy between the two.  
  
## See Also  
 [BTSNTSvc.exe.config File](../core/btsntsvc-exe-config-file.md)