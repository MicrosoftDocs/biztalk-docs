---
title: "Code Page Mappings | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 282b5c83-a583-46af-8cc0-80ad1a5e1c34
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Code Page Mappings
You can specify service-level and application-level code page mapping overrides. Also, you can specify code point mapping overrides within a defined code page. For more information, see Deployment.  
  
## Troubleshooting Tools  
  
### SQL Server tracing using Profiler  
 SQL Server Profiler is a graphical user interface to SQL Trace for monitoring an instance of the Database Engine or Analysis Services. You can capture and save data about each event to a file or table to analyze later. For more information, see [Introducing SQL Server Profiler](http://go.microsoft.com/fwlink/?LinkID=180433) (http://go.microsoft.com/fwlink/?LinkID=180433).  
  
### DB2 provider tracing using HIS Trace Utility  
 The Provider Trace Utility captures and saves information from the Microsoft client for DB2 network connections, OLE DB interfaces and data messages. For more information, see the Host Integration Server 2009 [Trace Utility Help](http://go.microsoft.com/fwlink/?LinkID=180447) (http://go.microsoft.com/fwlink/?LinkID=180447) and [SNA Trace Utility](http://go.microsoft.com/fwlink/?LinkID=180449) (http://go.microsoft.com/fwlink/?LinkID=180449).  
  
### Network tracing using Network Monitor  
 The Network Monitor captures network traffic for display and analysis. It enables you to perform tasks such as analyzing previously captured data in user-defined methods, extracting data from defined protocol parsers. It includes a Distributed Data Management (DDM) parser for use with the Data Provider. Contact Microsoft Customer Support Services for a copy of the DDM parser. For more information, see [Network Monitor](http://go.microsoft.com/fwlink/?LinkID=180448) (http://go.microsoft.com/fwlink/?LinkID=180448).  
  
### DB2 server tracing using IBM tools  
 For more information, see the IBM DB2 Administration Guide for the applicable DB2 platform and version.  
  
### Windows Server events using Event Viewer  
 Enterprise Single Sign-On utilizes the Windows Application event log. The Event Viewer is a Microsoft Management Console (MMC) snap-in that enables you to browse and manage event logs. For more information, see [Event Viewer](http://go.microsoft.com/fwlink/?LinkID=131274) (http://go.microsoft.com/fwlink/?LinkID=131274).  
  
### Event Tracing for Windows using Performance Monitor  
 The DRDA Service ETW (Event Tracing for Windows) trace listener operates as an ETW provider to output trace data to a Windows ETW controller for access by ETW consumers. The Windows Performance Monitor uses performance counters, event trace data, and configuration information, which can be combined into Data Collector Sets. For more information, see [Performance Monitor](http://technet.microsoft.com/library/cc749249.aspx) (http://technet.microsoft.com/library/cc749249.aspx).  
  
#### Start Event Trace Session  
 The Windows administrator must start a DRDA Service ETW event trace session using Performance Monitor or the logman command line utility.  
  
1. On the **Start** menu, point to **All Programs**, point to **Microsoft Visual Studio**, point to **Visual Studio Tools**, right **click Visual Studio x64 Win64 Command Prompt**, and click **Run as administrator**. The **User Account Control** dialog may appear. Click **Yes** to continue.  
  
2. In the **Visual Studio x64 Win64 Command Prompt** window, locate the installation folder in which you downloaded the installation program, **logman start MsDrdaService -p {3B4388CE-50E0-404C-A62B-E9C87D4F3BC4} -o c:\temp\MsDrdaServiceETW.etl -ets**, and then click **Enter**.  
  
   ```  
   C:\Program Files (x86)\Microsoft Visual Studio 10.0\VC>logman start MsDrdaService -p {3B4388CE-50E0-404C-A62B-E9C87D4F3BC4} -o c:\temp\MsDrdaServiceETW.etl -ets  
   The command completed successfully.  
   ```  
  
    <em>**Example 1.</em>* Start ETW event trace session command line argument with example property values.*  
  
#### Stop Event Trace Session  
 The Windows administrator can stop a DRDA Service ETW event trace session using Performance Monitor or the logman command line utility.  
  
1. On the **Start** menu, point to **All Programs**, point to **Microsoft Visual Studio**, point to **Visual Studio Tools**, right click **Visual Studio x64 Win64 Command Prompt**, and click **Run as administrator**. The **User Account Control dialog** may appear. Click **Yes** to continue.  
  
2. In the **Visual Studio x64 Win64 Command Prompt** window, locate the installation folder in which you downloaded the installation program, **logman stop MsDrdaService -ets**, and then click **Enter**.  
  
   ```  
   C:\Program Files (x86)\Microsoft Visual Studio 10.0\VC>logman stop MsDrdaService -ets  
   The command completed successfully.  
   ```  
  
    <em>**Example 2.</em>* Stop ETW event trace session command line argument with example property values.*  
  
#### Format Event Trace Session Data  
 The Windows administrator can format DRDA Service ETW event trace session data using [Service Trace Viewer Tool (SvcTraceViewer.exe)](https://docs.microsoft.com/en-us/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe) or the tracerpt command line utility.  
  
1. On the **Start** menu, point to **All Programs**, point to **Microsoft Visual Studio**, point to **Visual Studio Tools**, right click **Visual Studio x64 Win64 Command Prompt**, and click **Run as administrator**. The **User Account Control dialog** may appear. Click **Yes** to continue.  
  
2. In the **Visual Studio x64 Win64 Command Prompt** window, locate the installation folder in which you downloaded the installation program, **tracerpt c:\temp\MsDrdaServiceETW.etl**, and then click **Enter**.  
  
   ```  
   C:\temp>tracerpt c:\temp\MsDrdaServiceETW.etl  
   Input  
   ----------------  
   File(s):  
        c:\temp\MsDrdaServiceETW.etl  
   100.00%  
   Output  
   ----------------  
   DumpFile:           dumpfile.xml  
   Summary:            summary.txt  
   The command completed successfully.  
  
   ```  
  
    <em>**Example 3.</em>* Format ETW event trace session data command line argument with example property values.*