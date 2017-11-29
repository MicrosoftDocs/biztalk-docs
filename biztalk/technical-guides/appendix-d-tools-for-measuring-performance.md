---
title: "Appendix D: Tools for Measuring Performance | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 024f4a08-f3fd-4786-8549-0da5463c0bb9
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Appendix D: Tools for Measuring Performance
This topic describes several tools that can be used to monitor and evaluate the performance of a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.  
  
## Performance Analysis of Logs (PAL) tool  
 The PAL tool is used to generate an HTML-based report that graphically charts important performance monitor counters and generates alerts when thresholds for these counters are exceeded. PAL is an excellent tool for identifying bottlenecks in a BizTalk Server solution to facilitate the appropriate allocation of resources when optimizing the performance of the solution. For more information about the Performance Analysis of Logs (PAL) tool, see [http://go.microsoft.com/fwlink/?LinkID=98098](http://go.microsoft.com/fwlink/?LinkID=98098).  
  
> [!NOTE]  
>  Use of this tool is not supported by Microsoft, and Microsoft makes no guarantees about the suitability of this programs. Use of this program is entirely at your own risk.  
  
## Performance Monitor  
 Performance Monitor provides a visual display of built-in Windows performance counters, either in real time or as a way to review historical data.  
  
## Log Parser  
 Log parser is a powerful, versatile tool that provides universal query access to text-based data such as log files, XML files and CSV files, as well as key data sources on the Windows® operating system such as the Event Log, the Registry, the file system, and Active Directory®. Log Parser is available for download at [http://go.microsoft.com/fwlink/?LinkID=100882](http://go.microsoft.com/fwlink/?LinkID=100882).  
  
## Relog  
 The Relog utility is used to extract performance counters from logs created by Performance Monitor and convert the data into other formats, such as tab-delimited text files (text-TSV), comma-delimited text files (text-CSV), binary files, and SQL databases. This data can then be analyzed and queried using other tools, such as Log Parser, to generate statistics for key performance indicators (KPIs). The Relog utility is provided with [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] and subsequent versions.  
  
## LoadGen  
 BizTalk LoadGen 2007 is a load generation tool used to run performance and stress tests against BizTalk Server. The Microsoft BizTalk LoadGen 2007 tool is available for download at [http://go.microsoft.com/fwlink/?LinkId=59841](http://go.microsoft.com/fwlink/?LinkId=59841).  
  
## Visual Studio Team System 2008 Load Testing  
 The Visual Studio Team System (VSTS) 2008 provides a tool for creating and running load tests. For more information about working with load tests see [http://go.microsoft.com/fwlink/?LinkId=141486](http://go.microsoft.com/fwlink/?LinkId=141486).  
  
## BizUnit  
 BizUnit is a framework designed for automated testing of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solutions. BizUnit is an excellent tool for testing end-to-end BizTalk Server scenarios. For more information about BizUnit 3.0, see [http://go.microsoft.com/fwlink/?LinkID=85168](http://go.microsoft.com/fwlink/?LinkID=85168).  
  
> [!NOTE]  
>  Use of this tool is not supported by Microsoft, and Microsoft makes no guarantees about the suitability of this programs. Use of this program is entirely at your own risk.  
  
## IOMeter  
 IOMeter is an open source tool used for measuring disk I/O performance. For more information about IOMeter, see [http://go.microsoft.com/fwlink/?LinkId=122412](http://go.microsoft.com/fwlink/?LinkId=122412).  
  
> [!NOTE]  
>  Use of this tool is not supported by Microsoft, and Microsoft makes no guarantees about the suitability of this programs. Use of this program is entirely at your own risk.  
  
## BizTalk Server Orchestration Profiler  
 The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Orchestration Profiler is used to obtain a consolidated view of orchestration tracking data for a specified period of time. This provides developers with insight into how orchestrations are being processed and the level of test coverage that is being applied. The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Orchestration Profile helps to identify potential problems with latency and code path exceptions by highlighting long running and error prone orchestration shapes, which are critical for effective performance testing. The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Orchestration Profiler is available for download at [http://go.microsoft.com/fwlink/?LinkID=102209](http://go.microsoft.com/fwlink/?LinkID=102209).  
  
> [!NOTE]  
>  Use of this tool is not supported by Microsoft, and Microsoft makes no guarantees about the suitability of this programs. Use of this program is entirely at your own risk.  
  
## Pathping  
 Pathping provides information about possible data loss at one or more router hops on the way to a target host. To do so, pathping sends Internet Control Message Protocol (ICMP) packets to each router in the path. Pathping.exe is available with all versions of Windows since Windows 2000 Server.  
  
## SQL Server Tools for Performance Monitoring and Tuning  
 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] provides several tools for monitoring events in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] and for tuning the physical database design. These tools are described in the topic “Tools for Performance Monitoring and Tuning” in the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Books Online at [http://go.microsoft.com/fwlink/?LinkId=146357](http://go.microsoft.com/fwlink/?LinkId=146357). Information about specific tools used for [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] performance monitoring and tuning is provided below:  
  
### SQL Profiler  
 Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Profiler can be used to capture Transact-SQL statements that are sent to [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] and the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] result sets from these statements. Because [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] is tightly integrated with [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], the analysis of a [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Profile trace can be a useful tool for analyzing problems that may occur in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] when reading from and writing to [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] databases. For information about how to use [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Profiler, see "Using SQL Server Profiler" in the [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] Books Online at [http://go.microsoft.com/fwlink/?linkid=104423](http://go.microsoft.com/fwlink/?linkid=104423).  
  
> [!IMPORTANT]  
>  There is considerable overhead associated with running SQL Profiler. Therefore SQL Profiler is best suited for use in test or development environments. If using SQL Profiler to troubleshoot a production environment, be aware of the associated overhead costs and limit the use of SQL Profiler accordingly.  
  
> [!NOTE]  
>  When using SQL Profiler to capture Transact-SQL statements, configure SQL Profiler to generate output to a local drive rather than a drive located on a remote network share or other slow device, for example, a local USB memory stick.  
  
### SQL Trace  
 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] provides Transact-SQL system stored procedures to create traces on an instance of the SQL Server Database Engine. These system stored procedures can be used from within your own applications to create traces manually, instead of using SQL Server Profiler. This allows you to write custom applications specific to the needs of your enterprise. For more information about using SQL Trace, see “Introducing SQL Trace in the [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] Books Online at [http://go.microsoft.com/fwlink/?LinkId=146354](http://go.microsoft.com/fwlink/?LinkId=146354).  
  
> [!NOTE]  
>  When using SQL Trace to capture Transact-SQL statements, configure SQL Trace to generate output to a local drive rather than a drive located on a remote network share or other slow device, such as a USB flash drive.  
  
### SQL Activity Monitor  
 [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] Activity Monitor provides information about [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] processes and how these processes affect the current instance of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. For more information about [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] Activity Monitor, see “Activity Monitor” in the [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] Books Online at [http://go.microsoft.com/fwlink/?LinkId=146355](http://go.microsoft.com/fwlink/?LinkId=146355). For information about how to open Activity Monitor from [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Management Studio, see “How to: Open Activity Monitor ([!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Management Studio) in the [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] Books Online at [http://go.microsoft.com/fwlink/?LinkId=135094](http://go.microsoft.com/fwlink/?LinkId=135094).  
  
### SQL Server 2008 Data Collection  
 [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] provides a data collector that you can use to obtain and save data that is gathered from several sources. The data collector enables you to use data collection containers, which enable you to determine the scope and frequency of data collection on a computer that is running [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]. For more information about implementing [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] data collection, see “Data Collection” in the [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] Books Online at [http://go.microsoft.com/fwlink/?LinkId=146356](http://go.microsoft.com/fwlink/?LinkId=146356).  
  
### SQL Server 2005 Performance Dashboard Reports  
 [!INCLUDE[btsSQLServer2005](../includes/btssqlserver2005-md.md)] Performance Dashboard Reports are used to monitor and resolve performance problems on your [!INCLUDE[btsSQLServer2005](../includes/btssqlserver2005-md.md)] database server. For more information about [!INCLUDE[btsSQLServer2005](../includes/btssqlserver2005-md.md)] Performance Dashboard Reports, see [http://go.microsoft.com/fwlink/?LinkID=118673](http://go.microsoft.com/fwlink/?LinkID=118673).  
  
### SQLIO  
 The SQLIO tool was developed by Microsoft to evaluate the I/O capacity of a given configuration. As the name of the tool implies, SQLIO is a valuable tool for measuring the impact of file system I/O on [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] performance. SQLIO can be downloaded from [http://go.microsoft.com/fwlink/?LinkId=115176](http://go.microsoft.com/fwlink/?LinkId=115176).