---
title: "Troubleshooting BizTalk Server Performance | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dbf21fb9-1ae1-48b5-a65a-e96839b23945
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Troubleshooting BizTalk Server Performance
This section contains general guidelines for diagnosing and resolving performance problems related to the BizTalk Messaging Engine.  
  
## Estimating Document Processing Requirements  
 Plan and test to determine your Messaging Engine performance needs before deploying your solution into a production environment. This will help you build out your BizTalk Server and SQL Server environments appropriately.  
  
1.  Plan for overhead associated with any fault tolerance or backup and recovery needs  
  
    -   Will the SQL Server disks be configured as RAID arrays?  
  
    -   Will Windows Clustering be used for BizTalk Hosts, SQL Server, or Enterprise Single Sign-On? For more information see [Planning for High Availability](../core/planning-for-high-availability3.md).  
  
    -   Will Network Load Balancing be used?  
  
    -   What are the backup and recovery requirements for the environment? For more information, see [Backing Up and Restoring BizTalk Server Databases](../core/backing-up-and-restoring-biztalk-server-databases.md).  
  
2.  Follow the guidelines in [Planning for Sustained Performance](../core/planning-for-sustained-performance.md) to plan, test, and scale your BizTalk Server and SQL Server environment.  
  
3.  Follow the guidelines in [Tracking Performance Characteristics](../core/tracking-performance-characteristics.md) to plan for overhead associated with document tracking requirements.  
  
## Optimizing an Existing BizTalk Server Environment  
 Follow these steps to optimize an existing BizTalk Server environment:  
  
1.  Follow the guidelines in [Identifying Performance Bottlenecks](../core/identifying-performance-bottlenecks.md) to pinpoint possible bottlenecks in your BizTalk Server environment.  
  
2.  Follow the guidelines in [Optimizing Resource Usage Through Host Throttling](../core/optimizing-resource-usage-through-host-throttling.md) to maximize document throughput for the BizTalk Server environment.  
  
3.  Consider modifying the parameters documented in [Configuration Parameters that Affect Adapter Performance](../core/configuration-parameters-that-affect-adapter-performance.md) to maximize adapter performance in certain scenarios.  
  
4.  Follow the guidelines in [How BizTalk Server Processes Large Messages](../core/how-biztalk-server-processes-large-messages.md) to optimize Messaging Engine performance when processing Large Messages (more than 100 MB).  
  
5.  Create separate hosts and host instances for send adapters, receive adapters, and orchestrations. This will give each adapter a separate host instance to run in and will ensure that one adapter does not adversely affect another. Since host throttling settings are configurable at the host level, the separation of processing logic into different hosts will also permit you to configure throttling settings based upon the processing requirements of each host.  
  
## Diagnosing Performance Problems in an Existing BizTalk Server Environment  
 Typically a performance problem can be narrowed down to one of the following components of a BizTalk Server environment:  
  
- A receive adapter or the system that the adapter is receiving documents from. For example if documents are being received by the HTTP adapter at a suboptimal rate then the problem may be with the HTTP receive adapter or with the client that is posting to the HTTP adapter.  
  
- An orchestration service instance.  
  
- Performance of the Microsoft SQL server that houses the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases.  
  
- A send adapter or the system that the adapter is sending documents to. For example if documents are being sent by the SQL adapter at a suboptimal rate then the problem may be with the SQL send adapter or with the computer running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] that the SQL adapter is updating.  
  
  Use the following guidelines to help identify the components of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment that are performing poorly:  
  
- Capture any warnings or errors generated in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] or [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Event Viewer.  
  
- Follow the steps in [Identifying Performance Bottlenecks](../core/identifying-performance-bottlenecks.md) to help identify performance bottlenecks.  
  
  Once the poorly performing component has been identified, follow the appropriate guidelines to help resolve the issue:  
  
  **Guidelines for resolving performance problems related to send and receive adapters**  
  
- See [Troubleshooting BizTalk Server Adapters](../core/troubleshooting-biztalk-server-adapters.md) for general information to troubleshoot problems with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] adapters. This section contains general troubleshooting information including information about how to set up logging for certain adapters and information that can be used diagnose network problems, problems with MSDTC, problems with the registry, problems with the file system, and problems with IIS.  
  
- See the appropriate section of [Troubleshooting BizTalk Server Dependencies](../core/troubleshooting-biztalk-server-dependencies.md) for general information to troubleshoot problems with MSDTC, Certificates, Enterprise Single Sign-On, and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  
  
  **Guidelines for resolving performance problems related to orchestrations**  
  
- Modify the appropriate sections of the BTSNTSvc.exe.config file documented in [Orchestration Engine Configuration](../core/orchestration-engine-configuration.md).  
  
  **Guidelines for resolving performance problems related to SQL Server**  
  
- SQL Server Profiler can be used to capture Transact-SQL statements that are sent to SQL Server and the SQL Server result sets from these statements. Since BizTalk Server is tightly integrated with SQL Server, the analysis of a SQL Server Profile trace can be a useful tool for analyzing problems that may occur in BizTalk Server when reading from and writing to SQL Server databases. For information about how to use SQL Server Profiler see the SQL Server documentation.  
  
- The SQL Server Query Editor can be used to execute SQL statements directly against SQL Server databases. This functionality may be useful for querying the BizTalk Server databases or for updating the BizTalk Server databases in certain scenarios. For more information about Query Editor see the SQL Server documentation.  
  
- Review [Troubleshooting SQL Server](../core/troubleshooting-sql-server.md) for additional information.  
  
## See Also  
 [Troubleshooting](../core/troubleshooting.md)