---
title: "Scaling Your Solutions | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "performance, scaling"
  - "scaling, scaling out"
  - "scaling, performance"
  - "scaling, about scaling"
  - "scaling, scaling up"
  - "scaling"
ms.assetid: e2acbaa4-29d3-4c89-ac1f-c0641cfa0442
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Scaling Your Solutions
BizTalk Server architecture provides a very good support for scalability. The scaling patterns that you choose depend on complexity of your scenario, hardware and the throughput/Latency requirements. You should start with a smaller topology initially and try to scale-up or down based on the guidelines in this section.  
  
## Scaling Out and Scaling Up  
 There are two ways to scale your BizTalk Server system:  
  
- Scaling-out is the process of adding additional computers. For example, if BizTalk Server is bottlenecked by CPU resources, adding another server provides double the CPU resources which may provide double the throughput.  
  
- Scaling-up is process of upgrading the existing computer. For example, you can upgrade a BizTalk Server computer from a 4 processor machine to an 8 processor.  
  
  A BizTalk Server system has two tiers: the BizTalk Server tier and the SQL Server tier, which contains your MessageBox databases. In any scenario, you can scale out or scale up each tier. That is, you can scale-out BizTalk Server and the MessageBox database, or scale up both of them.  
  
  In most cases, the BizTalk tier becomes a bottleneck first, and you start improving performance by scaling it out. But, at some point, depending on complexity of your system and the hardware you use, you can’t scale out the BizTalk tier anymore and the SQL Server tier becomes the bottleneck. Then, you scale up the SQL Server tier, and next scale it out by adding more MessageBox databases.  
  
> [!NOTE]
>  A new MessageBox database does not necessarily mean another server here. A single SQL server can have multiple MessageBox databases. Also, multiple MessageBox databases incur DTC cost and network hop if the databases are on different computers.  
  
 In theory, the SQL Server tier can scale out indefinitely as long as the master MessageBox database is not saturated.  
  
 The topics in this section describe these scaling patterns in more detail. They also explain how to scale each pattern and how to determine when you can no longer use that pattern to scale your system.  
  
## In This Section  
  
-   [What Is Scalability?](../core/what-is-scalability.md)  
  
-   [Scaling Out the BizTalk Server Tier](../core/scaling-out-the-biztalk-server-tier.md)  
  
-   [Scaling Up the BizTalk Server Tier](../core/scaling-up-the-biztalk-server-tier.md)  
  
-   [Scaling Out the SQL Server Tier](../core/scaling-out-the-sql-server-tier.md)  
  
-   [Scaling Up the SQL Server Tier](../core/scaling-up-the-sql-server-tier.md)  
  
## See Also  
 [Scaled-Out Receiving Hosts](../core/scaled-out-receiving-hosts.md)   
 [Scaled-Out Processing Hosts](../core/scaled-out-processing-hosts.md)   
 [Scaled-Out Sending Hosts](../core/scaled-out-sending-hosts.md)   
 [Using Windows Server Cluster to Provide High Availability for BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md)   
 [Scaled-Out Databases](../core/scaled-out-databases.md)   
 [Clustering the BizTalk Server Databases](../core/clustering-the-biztalk-server-databases1.md)