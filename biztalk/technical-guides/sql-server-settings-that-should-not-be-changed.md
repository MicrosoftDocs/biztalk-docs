---
title: "SQL Server settings not to change | Microsoft Docs"
description: Max Degree of Parallelism, Auto create statistics Auto Update statistics, and rebuilding indexes in BizTalk Server
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4b383bfb-c3d9-47d4-b294-f6be94302734
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SQL Server Settings That Should Not Be Changed
When setting up [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] during the operational readiness procedures for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you should not make changes to the following settings.  
  
## SQL Server Max Degree of Parallelism  
 Max Degree of Parallelism (MDOP) is set to “1” during the configuration of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] for the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance(s) that host the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MessageBox database(s). This is a [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance-level setting. This setting should not be changed from the value of “1”. Changing this to anything other than “1” can have a significant negative impact on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] stored procedures and performance. If changing the parallelism setting for an instance of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] will have an adverse effect on other database applications that are being executed on the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance, you should create a separate instance of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] dedicated to hosting the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases.  
  
 Parallel queries are generally best suited to batch processing and decision support workloads. They are typically not desirable in a transaction processing environment where you have many short, fast queries running in parallel. In addition, changing the MDOP setting sometimes causes the query plan to be changed, which leads to poor query performance or even deadlocks with the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] queries.  
  
 The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] stored procedures provide the correct joins and lock hints wherever possible in order to try to keep the query optimizer from doing much work and changing the plan. These stored procedures provide consistent query executions by constructing the queries such that the query optimizer is taken out of the picture as much as possible.  
  
 For more information, see [KB 899000: Parallelism setting for SQL Server instance used by BizTalk Server](https://support.microsoft.com/help/899000/the-parallelism-setting-for-the-instance-of-sql-server-when-you-config).  
  
## SQL Server Statistics on the MessageBox Database  
 The following options are turned off by default in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MessageBox database when it is created:  
  
- Auto create statistics  
  
- Auto update statistics  
  
  Do not enable these options on MessageBox databases. Enabling the "auto create statistics" and "auto update statistics" options can cause undesirable query execution delays, especially in a high-load environment.  
  
  In addition, the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] stored procedures have exact joins and lock hints specified on the queries. This is done to ensure that the optimal query plan is used by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] queries in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. The distributions and expected results for the queries are known; the approximate number of rows returned is known. Statistics are generally not needed.  
  
  For more information, see the following Microsoft Knowledge Base articles:  
  
- **912262**—["The auto update statistics option, the auto create statistics option, and the Parallelism setting are turned off in the SQL Server database instance that hosts the BizTalk Server BizTalkMsgBoxDB database"](https://support.microsoft.com/help/912262/the-auto-update-statistics-option-the-auto-create-statistics-option-an).  
  
- **917845**—["You experience blocking, deadlock conditions, or other SQL Server issues when you try to connect to the BizTalkMsgBoxDb database in BizTalk Server"](https://support.microsoft.com/help/917845/you-experience-blocking--deadlock-conditions--or-other-sql-server-issu).  
  
## Changes to the MessageBox Database  
 The MessageBox database should be treated like non-Microsoft application source code. That is, you should not “tweak” the MessageBox database via changes to tables, indexes, stored procedures, and most SQL Server database settings. For more information, in the BizTalk Core Engine's WebLog, see [What you can and can't do with the MessageBox Database server](http://go.microsoft.com/fwlink/p/?LinkId=101577).  
  
## Default Settings for the Database Index Rebuilds and Defragmentation  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] does not support defragmenting indexes. “DBCC INDEXDEFRAG” and “ALTER INDEX … REORGANIZE …” are not supported since they use page locking, which can cause blocking and deadlocks with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] does support database index rebuilds (“DBCC DBREINDEX” and “ALTER INDEX … REBUILD …”), but they should only be done during maintenance windows when [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is not processing data. Index rebuilds while [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is processing data are not supported.  
  
 For more information, see [KB 917845: You experience blocking, deadlock conditions, or other SQL Server issues when you try to connect to the BizTalkMsgBoxDb database in BizTalk Server"](https://support.microsoft.com/help/917845/you-experience-blocking--deadlock-conditions--or-other-sql-server-issu).  
  
 Index fragmentation is not as much of a performance issue for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] as it would be for a DSS system or an OLTP system that performs index scans. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] does very selective queries and updates and [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] stored procedures should not cause table or index scans.  
  
 
## See Also  
 [Checklist: Configuring SQL Server](~/technical-guides/checklist-configuring-sql-server.md)
