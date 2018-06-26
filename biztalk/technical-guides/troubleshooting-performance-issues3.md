---
title: "Troubleshooting Performance Issues3 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7a348c4b-7df2-43e9-810c-1f538a97d7e1
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Troubleshooting Performance Issues
This section contains general guidelines for diagnosing and resolving performance problems related to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and its dependencies. These guidelines may also be used preemptively, to identify potential problems before they become critical issues.  
  
## Diagnosing Performance Problems in the BizTalk Server Environment  
 Typically a performance problem can be narrowed down to one of the following components of a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment:  
  
- A receive adapter or the system from which the adapter is receiving documents. For example, if documents are being received by the HTTP adapter at a suboptimal rate then the problem may be with the HTTP receive adapter or with the client that is posting to the HTTP adapter.  
  
- An orchestration service instance.  
  
- Performance of the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] that hosts the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases.  
  
- A send adapter or the system that the adapter is sending documents to. For example, if documents are being sent by the SQL adapter at a suboptimal rate then the problem may be with the SQL send adapter or with the computer running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] that the SQL adapter is updating.  
  
  Use the following guidelines to help identify the components of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment that are performing poorly:  
  
- Capture any warnings or errors generated in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] or [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Event Viewer.  
  
- Follow the steps in "Identifying Performance Bottlenecks" in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help at [http://go.microsoft.com/fwlink/?LinkId=154238](http://go.microsoft.com/fwlink/?LinkId=154238) to help identify performance bottlenecks.  
  
  Once the poorly performing component has been identified, follow the appropriate guidelines to help resolve the issue:  
  
  **Guidelines for resolving performance problems related to send and receive adapters**  
  
- For information about troubleshooting problems with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] adapters, see "Troubleshooting BizTalk Server Adapters" in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help at [http://go.microsoft.com/fwlink/?LinkId=154240](http://go.microsoft.com/fwlink/?LinkId=154240). This section contains general troubleshooting information including information about how to set up logging for certain adapters, and information that can be used diagnose network problems, problems with MSDTC, problems with the registry, problems with the file system, and problems with IIS.  
  
- For information about troubleshooting problems with MSDTC, certificates, Enterprise Single Sign-On, and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], see the appropriate section of "Troubleshooting BizTalk Server Dependencies" in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help at [http://go.microsoft.com/fwlink/?LinkId=154242](http://go.microsoft.com/fwlink/?LinkId=154242).  
  
  **Guidelines for resolving performance problems related to orchestrations**  
  
- For information about modifying the appropriate sections of the BTSNTSvc.exe.config file, see "Orchestration Engine Configuration" in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help at [http://go.microsoft.com/fwlink/?LinkId=154244](http://go.microsoft.com/fwlink/?LinkId=154244).  
  
  **Guidelines for resolving performance problems related to SQL Server**  
  
- SQL Server Profiler can be used to capture Transact-SQL statements that are sent to [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] and the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] result sets from these statements. Since [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is tightly integrated with [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], the analysis of a [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Profile trace can be a useful tool for analyzing problems that may occur in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] when reading from and writing to [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] databases. For information about how to use [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Profiler, see "Using SQL Server Profiler" in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Books Online at [http://go.microsoft.com/fwlink/?linkid=104423](http://go.microsoft.com/fwlink/?linkid=104423).  
  
- [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Management Studio can be used to execute SQL statements directly against [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] databases. This functionality may be useful for querying the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases or for updating the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases in certain scenarios. For more information about using SQL Server Management Studio to execute SQL statements, see "Writing, Analyzing, and Editing Scripts with SQL Server Management Studio" in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Books Online at [http://go.microsoft.com/fwlink/?linkid=104425](http://go.microsoft.com/fwlink/?linkid=104425).  
  
- For more information about resolving performance problem related to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, see "Troubleshooting SQL Server" in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help at [http://go.microsoft.com/fwlink/?LinkId=154250](http://go.microsoft.com/fwlink/?LinkId=154250).  
  
## See Also  
 [http://go.microsoft.com/fwlink/?linkid=104430](http://go.microsoft.com/fwlink/?linkid=104430)