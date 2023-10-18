---
description: "Learn more about: Tools and Utilities for Troubleshooting"
title: "Tools and Utilities for Troubleshooting"
ms.custom: ""
ms.date: "06/29/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Tools and Utilities for Troubleshooting
This topic describes several tools and utilities that can be useful for diagnosing the root cause of a problem in a Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] component or dependency.

|Troubleshooting|Tool|Use|
|---------------------|----------|---------|
|**SQL Server Troubleshooting**|SQL Activity Monitor|SQL Server 2008 Activity Monitor provides information about SQL Server processes and how these processes affect the current instance of SQL Server. For more information about SQL Server 2008 Activity Monitor, see [Activity Monitor](/previous-versions/sql/sql-server-2008-r2/cc879320(v=sql.105)) (https://go.microsoft.com/fwlink/?LinkId=146355) in the SQL Server documentation. For information about how to open Activity Monitor from SQL Server Management Studio, see [How to: Open Activity Monitor (SQL Server Management Studio)](/sql/relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio) (https://go.microsoft.com/fwlink/?LinkId=135094) in the SQL Server documentation.|
||SQL Server 2008 Data Collection|SQL Server 2008 provides a data collector that you can use to obtain and save data that is gathered from several sources. The data collector enables you to use data collection containers, which enable you to determine the scope and frequency of data collection on a computer that is running SQL Server 2008. For more information about implementing SQL Server 2008 data collection, see [Data Collection](/sql/relational-databases/data-collection/data-collection) (https://go.microsoft.com/fwlink/?LinkId=146356) in the SQL Server documentation.|
||**Performance-related Troubleshooting**|The Relog utility is used to extract performance counters from logs created by Performance Monitor and convert the data into other formats, such as tab-delimited text files (text-TSV), comma-delimited text files (text-CSV), binary files, and SQL databases. This data can then be analyzed and queried using other tools, such as Log Parser, to generate statistics for key performance indicators (KPIs). The Relog utility is provided with Windows Server 2003 and subsequent versions.|
|Windows Performance Analysis Tools||Windows Performance Tools are designed for analysis of a wide range of performance problems including application start times, boot issues, deferred procedure calls and interrupt activity (DPCs and ISRs), system responsiveness issues, application resource usage, and interrupt storms. For more information, see [Windows Performance Analysis Developer Center](https://go.microsoft.com/fwlink/?LinkId=139763) (https://go.microsoft.com/fwlink/?LinkId=139763).|
|Pathping||Pathping provides information about possible data loss at one or more router hops on the way to a target host. To do so, pathping sends Internet Control Message Protocol (ICMP) packets to each router in the path. Pathping.exe is available with all versions of Windows since Windows 2000 Server.|
|IOMeter||IOMeter is an open source tool used for measuring disk I/O performance. For more information, see  [IOMeter](https://go.microsoft.com/fwlink/?LinkId=122412) (https://go.microsoft.com/fwlink/?LinkId=122412). **Important:**  Use of this tool is not supported by Microsoft, and Microsoft makes no guarantees about the suitability of this programs. Use of this program is entirely at your own risk.|
|**General troubleshooting**|-   Event Viewer<br />-   Network Monitor<br />-   SQL Server Profiler<br />-   SQL Server Query Editor<br />-   DTCTester<br />-   DTCPing<br />-   Performance Console<br />-   RegMon<br />-   FileMon<br />-   Debug Diagnostics Tool of the IIS Diagnostics Toolkit|See [Tools and Utilities to Use for Troubleshooting](../core/tools-and-utilities-to-use-for-troubleshooting.md) (https://go.microsoft.com/fwlink/?LinkId=154416).|

## See Also
 [Tools for Testing](../technical-guides/tools-for-testing.md)
 [Checklist: Configuring BizTalk Server](~/technical-guides/checklist-configuring-biztalk-server.md)