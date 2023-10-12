---
description: "Learn more about: Tools and Utilities to Use for Troubleshooting"
title: "Tools and Utilities to Use for Troubleshooting"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Tools and Utilities to Use for Troubleshooting
This section describes several tools and utilities that can be useful for diagnosing the root cause of a problem in a Microsoft BizTalk Server component or dependency.

## Event Viewer
 BizTalk Server logs information, warnings, and errors to the Event Log of the BizTalk Server based computer. When troubleshooting problems in a BizTalk Server component or dependency, the Event logs should be the first place to look for information to help diagnose the problem.

## Network Monitor
 Use the Network Monitor utility to capture network traffic between BizTalk Server and remote clients or servers. Captured network traffic can then be analyzed to diagnose network related problems.

 Network Monitor is available on Windows Server. It's avialable to download at [Microsoft Network Monitor 3.4 (archive)](https://www.microsoft.com/download/details.aspx?id=4865).

## Fiddler Tool

Use Fiddler to record all HTTP traffic between BizTalk Server and remote clients or servers. Fiddler is compatible with Visual Studio Team Edition for Testers and allows you to save recordings as Web test files that can be added to Visual Studio Team Edition for Testers projects.

Fiddler might not support SSL, might not automatically track hidden fields, such as ViewState, and it might not filter out dependent requests.

Fiddler is 3rd party/partner tool available at [Telerik Fiddler](https://www.telerik.com/fiddler).

## SQL Server Profiler
 Microsoft SQL Server Profiler can be used to capture Transact-SQL statements that are sent to SQL Server and the SQL Server result sets from these statements. Since BizTalk Server is tightly integrated with SQL Server, the analysis of a SQL Server Profile trace can be a useful tool for analyzing problems that may occur in BizTalk Server when reading from and writing to SQL Server databases.

## SQL Server Query Editor
 SQL Server Query Editor can be used to execute SQL statements directly against SQL Server databases. This functionality may be useful for querying the BizTalk Server databases or for updating the BizTalk Server databases in certain scenarios.

## DTCTester
 Most BizTalk Server runtime operations require Microsoft Distributed Transaction Coordinator (MSDTC) support to ensure that the operations are transactionally consistent. If MSDTC transaction support is not available, then the associated BizTalk Server runtime operations cannot proceed. Use the `Test-Dtc` Windows PowerShell cmdlet to verify distributed transaction support across firewalls or against networks. It verifies transaction support against a SQL Server database and therefore requires that SQL Server is installed on one of the computers being tested. 

For more information, go to [Test-Dtc](/powershell/module/msdtc/test-dtc).

## DTCPing
 Use the DTCPing tool to verify distributed transaction support across firewalls or against networks. The DTCPing tool must be installed on both the client and server computer and is a good alternative to the DTCTester utility when SQL Server is not installed on either computer. For more information about using DTCPing to verify distributed transaction support see [How to troubleshoot MS DTC firewall issues](./troubleshooting-problems-with-msdtc.md).

## Performance Console
 Use the Performance Console to capture performance monitoring data in your BizTalk Server environment. See [Performance Counters](../core/performance-counters.md) for a comprehensive list of the performance counters included with BizTalk Server.

## RegMon, FileMon, and DebugView
 RegMon displays registry access activity in real time, listing each call to the registry that an application makes, and logging the outcome. This tool allows you to identify when an application cannot access a registry key. Similarly, FileMon displays file system activity in real time, listing each system call that an application makes and registering the outcome. Debugview lets you monitor debug output on your local system, or any computer on the network that you can reach via TCP/IP.

 RegMon and FileMon enable administrators to test an application and to identify the failure of any calls that the application makes to the registry or file system. The administrator can then mitigate that failure, for example, by changing file system or registry key permissions.

 DebugView enables administrators to test an application and monitor debug output on your local system, or any computer on the network that you can reach via TCP/IP.

 For more information about these utilities, see [Windows Sysinternals](/sysinternals/).

## Debug Diagnostics Tool of the IIS Diagnostics Toolkit
 The Debug Diagnostic Tool of the IIS Diagnostics toolkit can generate a memory dump of a failing process and perform a basic analysis of the generated dump file. For more information about using the Debug Diagnostics Tool of the IIS Diagnostic Toolkit to capture a memory dump see [How to Capture a Memory Dump of a BizTalk Process](../core/how-to-capture-a-memory-dump-of-a-biztalk-process.md).