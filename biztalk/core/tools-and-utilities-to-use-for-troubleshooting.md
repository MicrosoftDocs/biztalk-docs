---
title: "Tools and Utilities to Use for Troubleshooting | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c817384f-e328-439d-9c41-a94ed75670ce
caps.latest.revision: 23
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Tools and Utilities to Use for Troubleshooting
This section describes several tools and utilities that can be useful for diagnosing the root cause of a problem in a Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] component or dependency.  
  
## Event Viewer  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] logs information, warnings, and errors to the Event Log of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] based computer. When troubleshooting problems in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] component or dependency, the Event logs should be the first place to look for information to help diagnose the problem. For more information about Event Viewer see the Windows documentation.  
  
## Network Monitor  
 Use the Network Monitor utility to capture network traffic between [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and remote clients or servers. Captured network traffic can then be analyzed to diagnose network related problems.  
  
 Network Monitor is available on [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] through the **Add/Remove Windows Components** option that is available in **Add/Remove Programs**.  
  
 Network Monitor functionality is provided for Windows XP through the use of the NETCAP.exe utility that is installed with the Windows Support Tools available on the Windows XP CD. For more information about the NETCAP.exe utility see [Description of the Network Monitor Capture Utility](http://go.microsoft.com/fwlink/?LinkId=66227).  
  
 For information about how to capture network traffic with Network Monitor see [How to capture network traffic with Network Monitor](http://go.microsoft.com/fwlink/?LinkId=66230).  
  
## Fiddler Tool  
 Use Fiddler to record all HTTP traffic between [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and remote clients or servers. Fiddler is compatible with Visual Studio Team Edition for Testers and allows you to save recordings as Web test files that can be added to Visual Studio Team Edition for Testers projects.  
  
 The disadvantages of Fiddler are that it does not currently support SSL, it does not automatically track hidden fields, such as ViewState, and it does not filter out dependent requests.  
  
 Fiddler is available at [http://www.fiddlertool.com](http://go.microsoft.com/fwlink/?LinkId=119605). For more information about how to use Fiddler, see [http://go.microsoft.com/fwlink/?LinkId=84814](http://go.microsoft.com/fwlink/?LinkId=84814).  
  
## SQL Server Profiler  
 Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Profiler can be used to capture Transact-SQL statements that are sent to [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] and the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] result sets from these statements. Since [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is tightly integrated with [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], the analysis of a [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Profile trace can be a useful tool for analyzing problems that may occur in BizTalk Server when reading from and writing to [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] databases. For information about how to use [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Profiler see the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] documentation.  
  
## SQL Server Query Editor  
 SQL Server Query Editor can be used to execute SQL statements directly against SQL Server databases. This functionality may be useful for querying the BizTalk Server databases or for updating the BizTalk Server databases in certain scenarios. For more information about Query Editor see the [!INCLUDE[btsSQLServer2005](../includes/btssqlserver2005-md.md)] or [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] documentation.  
  
## DTCTester  
 Most BizTalk Server runtime operations require Microsoft Distributed Transaction Coordinator (MSDTC) support to ensure that the operations are transactionally consistent. If MSDTC transaction support is not available, then the associated BizTalk Server runtime operations cannot proceed. Use the DTCTester tool to verify distributed transaction support across firewalls or against networks. The DTCTester utility uses ODBC to verify transaction support against a SQL Server database and therefore requires that SQL Server is installed on one of the computers being tested. For more information about DTCTester see [How To Use DTCTester Tool](http://support.microsoft.com/kb/293799).  
  
## DTCPing  
 Use the DTCPing tool to verify distributed transaction support across firewalls or against networks. The DTCPing tool must be installed on both the client and server computer and is a good alternative to the DTCTester utility when SQL Server is not installed on either computer. For more information about using DTCPing to verify distributed transaction support see [How to troubleshoot MS DTC firewall issues](http://go.microsoft.com/fwlink/?LinkId=61915).  
  
## Performance Console  
 Use the Performance Console to capture performance monitoring data in your BizTalk Server environment. See [Performance Counters](../core/performance-counters.md) for a comprehensive list of the performance counters included with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. For more information about using Performance Console see the Windows documentation.  
  
## RegMon, FileMon, and DebugView  
 RegMon displays registry access activity in real time, listing each call to the registry that an application makes, and logging the outcome. This tool allows you to identify when an application cannot access a registry key. Similarly, FileMon displays file system activity in real time, listing each system call that an application makes and registering the outcome. Debugview lets you monitor debug output on your local system, or any computer on the network that you can reach via TCP/IP.  
  
 RegMon and FileMon enable administrators to test an application and to identify the failure of any calls that the application makes to the registry or file system. The administrator can then mitigate that failure, for example, by changing file system or registry key permissions.  
  
 DebugView enables administrators to test an application and monitor debug output on your local system, or any computer on the network that you can reach via TCP/IP.  
  
 For more information about these utilities, see the Windows Sysinternals Web site at [http://www.microsoft.com/technet/sysinternals/default.mspx](http://go.microsoft.com/fwlink/?LinkId=66235).  
  
## Debug Diagnostics Tool of the IIS Diagnostics Toolkit  
 The Debug Diagnostic Tool of the IIS Diagnostics toolkit can generate a memory dump of a failing process and perform a basic analysis of the generated dump file. For more information about using the Debug Diagnostics Tool of the IIS Diagnostic Toolkit to capture a memory dump see [How to Capture a Memory Dump of a BizTalk Process](../core/how-to-capture-a-memory-dump-of-a-biztalk-process.md).