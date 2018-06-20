---
title: "Best Practices for BizTalk Server Settings | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e62024e1-f502-45a8-932f-edd8460bcf5f
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Best Practices for BizTalk Server Settings
This topic lists best practices that you should follow as you perform operational readiness procedures for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 **Configure message batching to increase adapter performance**  
  
- Minimize the number of transactions performed by an adapter by combining more than one operation into a single batch.  
  
- Limit the batch size based on the total number of bytes in the batch, in addition to message count. For more information about limiting the batch size, see [Configuring Batching to Improve Adapter Performance](../technical-guides/configuring-batching-to-improve-adapter-performance.md).  
  
  **Adjust the large message threshold**  
  
- To improve throughput, increase the large message threshold, which lowers the number of large messages that are buffered to disk during mapping.  
  
  **Determine the information you need to track during planning**  
  
- You should decide during the planning stages which information you need to track. This way, after you deploy the project, you can set the tracking options and limit the amount of tracked data to give you only the information you need.  
  
  > [!NOTE]  
  >  For more information about best practices related to tracking, see [Planning for Tracking](../technical-guides/planning-for-tracking.md) in this guide and [Health and Activity Tracking](http://go.microsoft.com/fwlink/p/?LinkId=154187) (http://go.microsoft.com/fwlink/p/?LinkId=154187).  
  
  **Do not track all messages**  
  
- We recommend that you not track all messages. This is because each time a message is touched, BizTalk Server makes another copy of the message. You can instead narrow the scope by tracking only a specific port. This helps to maximize the performance of your system and to keep the databases uncluttered.  
  
  **Set tracking on send ports and receive ports instead of on a pipeline**  
  
- If you set tracking options on pipelines, you will also set the tracking options globally for every port that uses the pipeline. This in turn may result in far more data being tracked than you intend, which will slow system performance. Instead, you can set tracking options on send ports and receive ports.  
  
  **Adjust throttling based on resource utilization**  
  
- Throttling in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is configured by default to provide good protection for the system. Monitor the performance counters for throttling states to see if throttling is taking place. Then gauge for yourself if the resource on which throttling is based (for example, database size or memory usage) is under or over utilized. Next, adjust the throttling thresholds up or down accordingly. For more information, see [Adjusting Throttling Thresholds: When and Why](http://go.microsoft.com/fwlink/p/?LinkId=154188) (<http://go.microsoft.com/fwlink/p/?LinkId=154188>).  
  
  **Use the PassThruTransmit pipeline if possible**  
  
- If no document processing is required before sending a message to its destination, use the PassThruTransmit pipeline instead of the XML send pipeline.  
  
  **Minimize usage of orchestration “Shape start and end” tracking events**  
  
- While orchestration shape tracking has obvious benefits for orchestration debugging, it has performance and scalability implications. The **Shape start and end** tracking event can cause significant overhead. It is best to minimize its usage in production environments where high throughput is necessary.  
  
  > [!NOTE]  
  >  **Shape start and end** tracking events are ENABLED by default on all orchestrations.  
  
## See Also  
 [Checklist: Configuring BizTalk Server](../technical-guides/checklist-configuring-biztalk-server.md)