---
title: "Reviewing and Testing SQL Server Cluster Configuration for Failover Scenarios | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5dbeb383-5b38-4467-acf8-2a5b244e5fa9
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Reviewing and Testing SQL Server Cluster Configuration for Failover Scenarios
Windows Clustering and SQL Server allow you to run SQL Server in Active/Active mode where each node of the cluster is “active” and running one or more SQL Server instances. This would allow you, for example, to have the MessageBox database on one node and all other [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases on the other node. This allows you to maximize cluster hardware usage.  
  
 If you use this configuration, however, you must verify that each node can simultaneously handle the load of all SQL Server instances during a SQL Server cluster node failover.  
  
## Evaluating Failover for an Active/Active Cluster  
 Considerations when verifying that a single node can handle the load of all SQL Server instances in the event of a SQL Server cluster node failover include:  
  
- Does the failover node have sufficient CPU resources?  
  
- Does the failover node have sufficient memory?  
  
- Is there sufficient network bandwidth?  
  
- Can the failover node handle the increased disk I/O contention?  
  
  The following scenarios should be evaluated when testing failover:  
  
- Power failure on the active server  
  
- Power failure on the passive server  
  
- Loss of disk connection  
  
- Broken public network connection on the Active node  
  
- Broken private network connection on the Active node  
  
- Broken public network connection on the Passive node  
  
- Broken private network connection on the Passive node  
  
- Failed SQL Server service  
  
- Failed SQL Server Agent service  
  
## Using an Active/Active/Passive Cluster  
 If you determine that one node cannot handle all SQL Server instances in a failover scenario, an alternative is to use an Active/Active/Passive clustering model. The Active/Active/Passive clustering model greatly increases the likelihood that there will always be one Passive node available for failover scenarios.  
  
## See Also  
 [Checklist: Configuring SQL Server](~/technical-guides/checklist-configuring-sql-server.md)