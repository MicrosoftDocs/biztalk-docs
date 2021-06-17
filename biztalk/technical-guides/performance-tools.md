---
title: "Performance Tools | Microsoft Docs"
description: Investigate BizTalk Server performance issues using BizUnit, IOMeter, Orchestration profiler, Log Parser, LoadGen, and SQL tools
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6d26c17a-3eb9-41a5-b0dc-31b974bf3d9b
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Performance Tools
This topic provides information on tools you can use to evaluate the performance of a BizTalk Server solution. The tools described in this topic have different purposes; some are designed to evaluate end-to-end performance while others focus on evaluating performance of a particular aspect of a BizTalk Server solution.

## BizUnit and BizUnit Designer
 BizUnit is a framework designed for automated testing of BizTalk solutions. BizUnit is an excellent tool for testing end-to-end BizTalk Server scenarios. Performing automated testing of BizTalk solutions with BizUnit is the primary focus of the [Implementing Automated Testing](../technical-guides/implementing-automated-testing.md) section of this guide. See [BizUnit](https://github.com/BizUnit/BizUnit).

 BizUnit Designer is a GUI that allows for rapid creation of BizUnit test cases that can be used for unit testing or system testing distributed applications. The tool is available at [BizUnit Designer](https://go.microsoft.com/fwlink/?LinkID=117917).

> [!NOTE]
>  Use of this tool is not supported by Microsoft, and Microsoft makes no guarantees about the suitability of this programs. Use of this program is entirely at your own risk.

## IOMeter
 IOMeter is an open source tool used for measuring disk I/O performance. See [http://www.iometer.org](http://www.iometer.org/).

> [!NOTE]
>  Use of this tool is not supported by Microsoft, and Microsoft makes no guarantees about the suitability of this programs. Use of this program is entirely at your own risk.

## Log Parser
 Log parser is a powerful, versatile tool that provides universal query access to text-based data such as log files, XML files and CSV files, as well as key data sources on the Windows® operating system such as the Event Log, the Registry, the file system, and Active Directory®. Download [Log Parser](https://www.microsoft.com/download/details.aspx?id=24659).

## Microsoft BizTalk LoadGen
 BizTalk LoadGen is a load generation tool used to run performance and stress tests against BizTalk Server. Download [BizTalk LoadGen 2007 Tools](https://www.microsoft.com/download/details.aspx?id=14925).

## Pathping
 Pathping provides information about possible data loss at one or more router hops on the way to a target host. To do so, pathping sends Internet Control Message Protocol (ICMP) packets to each router in the path. Pathping.exe is available with all versions of Windows since Windows 2000 Server.

## Performance Analysis of Logs (PAL)
 The PAL tool is used to generate an HTML-based report that graphically charts important performance counters and generates alerts when thresholds for these counters are exceeded. PAL is an excellent tool for identifying bottlenecks in a BizTalk Server solution to facilitate the appropriate allocation of resources when optimizing the performance of the solution.

 For more information about the Performance Analysis of Logs (PAL) tool, see [Performance Analysis of Logs (PAL) Tool](https://github.com/clinthuffman/PAL).

> [!NOTE]
>  Use of this tool is not supported by Microsoft, and Microsoft makes no guarantees about the suitability of this programs. Use of this program is entirely at your own risk.

## Performance Monitor
 Performance Monitor provides a visual display of built-in Windows performance counters, either in real time or as a way to review historical data.

## Relog
 The Relog utility is used to extract performance counters from logs created by Performance Monitor and convert the data into other formats, such as tab-delimited text files (text-TSV), comma-delimited text files (text-CSV), binary files, and SQL databases. This data can then be analyzed and queried using other tools, such as Log Parser, to generate statistics for key performance indicators (KPIs).

## Visual Studio - Testing the Application
 Both Microsoft Visual Studio Ultimate and Professional includes testing to help you define and manage your testing effort by using test plans. See [Testing the Application](/vsts/manual-test/overview).

## Visual Studio Profiling Tools
 The Visual Studio Profiling Tools allows you to profile custom .NET components (custom pipeline components, helper components invoked by pipelines and\or orchestrations, custom functoids). See, [Analyzing Application Performance by Using Profiling Tools](/visualstudio/profiling/performance-explorer).

## Windows Performance Analysis Tools
Windows Performance Tools are designed for analysis of a wide range of performance problems including application start times, boot issues, deferred procedure calls and interrupt activity (DPCs and ISRs), system responsiveness issues, application resource usage, and interrupt storms.

See [Windows Performance Analysis](/windows-hardware/test/weg/performance-tools).

## SQL Server Tools for Performance Monitoring and Tuning
 SQL Server provides several tools for monitoring events in SQL Server and for tuning the physical database design. See [Performance Monitoring and Tuning Tools](/sql/relational-databases/performance/performance-monitoring-and-tuning-tools).

### SQL Profiler
 Microsoft SQL Server Profiler can be used to capture Transact-SQL statements that are sent to SQL Server and the SQL Server result sets from these statements. Because SQL Server is tightly integrated with SQL Server, the analysis of a SQL Server Profile trace can be a useful tool for analyzing problems that may occur in BizTalk Server when reading from and writing to SQL Server databases. See [Using SQL Server Profiler](/sql/tools/sql-server-profiler/sql-server-profiler-templates-and-permissions).

> [!IMPORTANT]
>  There is considerable overhead associated with running SQL Profiler. Therefore SQL Profiler is best suited for use in test or development environments. If using SQL Profiler to troubleshoot a production environment, be aware of the associated overhead costs and limit the use of SQL Profiler accordingly.
>
>  When using SQL Profiler to capture Transact-SQL statements, configure SQL Profiler to generate output to a local drive rather than a drive located on a remote network share or other slow device, for example, a local USB memory stick.

### SQL Trace
 SQL Server provides Transact-SQL system stored procedures to create traces on an instance of the SQL Server Database Engine. These system stored procedures can be used from within your own applications to create traces manually, instead of using SQL Server Profiler. This allows you to write custom applications specific to the needs of your enterprise. See [SQL Trace](/sql/relational-databases/sql-trace/sql-trace).

> [!NOTE]
>  When using SQL Trace to capture Transact-SQL statements, configure SQL Trace to generate output to a local drive rather than a drive located on a remote network share or other slow device, such as a USB flash drive.

### SQL Activity Monitor
SQL Server Activity Monitor provides information about SQL Server processes and how these processes affect the current instance of SQL Server. See [Activity Monitor](/sql/relational-databases/performance-monitor/activity-monitor), and [How to: Open Activity Monitor (SQL Server Management Studio](/sql/relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio).

### SQL Server Data Collection
SQL Server provides a data collector that you can use to obtain and save data that is gathered from several sources. The data collector enables you to use data collection containers, which enable you to determine the scope and frequency of data collection on a computer that is running SQL Server. See [Data Collection](/sql/relational-databases/data-collection/data-collection).

### SQLIO
 The SQLIO tool was developed by Microsoft to evaluate the I/O capacity of a given configuration. As the name of the tool implies, SQLIO is a valuable tool for measuring the impact of file system I/O on SQL Server performance. Download [SQLIO](https://www.microsoft.com/download/details.aspx?id=20163).

## See Also
 [Finding and Eliminating Bottlenecks](../technical-guides/finding-and-eliminating-bottlenecks.md)