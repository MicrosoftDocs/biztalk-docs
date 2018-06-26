---
title: "Tracing | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3d538414-8ed2-4feb-91c1-c0ac4e201324
caps.latest.revision: 2
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Tracing
There are multiple options for tracing, which can help to capture problems in the data consumer application, OLE DB service components, Data Provider, DB2 network client, and DB2 database server.  
  
## SQL consumer tracing using SQL Server Profiler  
 SQL Server Profiler is a graphical user interface to SQL Trace for monitoring an instance of the Database Engine or Analysis Services. You can capture and save data about each event to a file or table to analyze later. For more information, see [Introducing SQL Server Profiler](http://go.microsoft.com/fwlink/?LinkID=241520) (http://go.microsoft.com/fwlink/?LinkID=241520).  
  
## Network tracing using Network Monitor  
 The Network Monitor captures network traffic for display and analysis. It enables you to perform tasks such as analyzing previously captured data in user-defined methods, extracting data from defined protocol parsers. It includes a Distributed Data Management (DDM) parser for use with the Data Provider. Contact Microsoft Customer Support Services for a copy of the DDM parser. For more information, see [Network Monitor](http://go.microsoft.com/fwlink/?LinkID=180448) (http://go.microsoft.com/fwlink/?LinkID=180448).  
  
## DB2 server tracing using IBM tools  
 For more information, see the IBM DB2 Administration Guide for the applicable DB2 platform and version.  
  
## Windows Server events using Event Viewer  
 The Event Viewer is a Microsoft Management Console (MMC) snap-in that enables you to browse and manage event logs. For more information, see [Event Viewer](http://go.microsoft.com/fwlink/?LinkID=131274) (http://go.microsoft.com/fwlink/?LinkID=131274).  
  
## DB2 provider tracing using Provider Trace Utility  
 The Provider Trace Utility captures and saves information from the Microsoft client for DB2 network connections, OLE DB interfaces and data messages. The Trace Utility allows the IT Professional to trace information related to a single trace component, which is the Data Provider’s underlying DRDA Application Requester client (DB2 Network Library).  
  
### Trace File Names  
 Each trace file has two names associated with it, \< *Filename* 1>.atf and \<*Filename* 2>.atf.  
  
 Traces are written to the first file until it reaches the specified size, then to the second until it reaches that size, and so on alternating between the two files.  
  
 By default, the trace files are stored in the \Program Files\Microsoft OLE DB Provider for DB2\Traces folder, with an .atf file name extension.  
  
 The following table lists the file names by component and type:  
  
|Component|Type of tracing|File names used|File names used|  
|---------------|---------------------|---------------------|---------------------|  
|**DB2 Network Library**|Internal|db2int1.atf|db2int2.atf|  
||Message|db2msg1.atf|db2msg2.atf|  
||API|db2api1.atf|db2api2.atf|  
  
### Choosing a Trace Type  
 After selecting the component to be traced, decide the type of tracing to apply.  
  
 The following table describes the types of tracing available:  
  
|Type of tracing|Activity traced|Applies to installed components|  
|---------------------|---------------------|-------------------------------------|  
|Internal*|Activity within a software component.|DB2 Network Library (DRDA AR client)|  
|Message|Messages passed into and out of a software component, including messages sent to and received from the network.|DB2 Network Library (DRDA AR client)|  
|API|Information passed into and out of a component DLL on the same computer.|DB2 Network Library (DRDA AR client)|  
  
 \* Internal tracing is intended for use by product support technicians. Interpreting internal traces and certain types of message traces requires a specialized knowledge base.  
  
### Trace Types  
 Before setting up tracing, decide the software components you want to trace, and which types of tracing information will be useful.  
  
 Each type of tracing is enabled using the Data Provider Trace Utility application.  
  
 **Internal Trace** types:  
  
- Fatal Conditions  
  
- Error Conditions  
  
- Debug Conditions  
  
- Function Entry/Exit  
  
- State Transition  
  
- Custom Conditions  
  
  **Message Trace** types:  
  
- Internal Messages  
  
- Connection Info  
  
- Network Data Streams  
  
  **API Trace** types:  
  
- OLEDB API  
  
- Network API (DRDA)  
  
### Message Traces  
 The following table details Message traces.  
  
|Trace option|Activity traced for Host Integration Server Applications on Host Integration Server client computers|  
|------------------|----------------------------------------------------------------------------------------------------------|  
|Internal Messages|Messages within the DB2 Network Library and its subcomponents|  
|Connection Info|Connection settings used by the DB2 Network Library (DRDA AR client) to connect with the DB2 Server (DRDA AS)|  
|Network Data Streams|Messages between DB2 Network Library (DRDA AR client) and DB2 Server (DRDA AS)|  
  
### Using the HIS Trace Utility  
 To start tracing:  
  
 On the **Start** menu, point to **Microsoft OLE DB Provider for DB2 Version 5.0**, and then point to **Trace Utility**.  
  
1. In the **Trace Items** dialog of the **HIS Trace Utility**, click **Properties**.  
  
2. In the **Internal Trace** dialog, click **Set All**, and then click **Message Trace**.  
  
3. In the **Message Trace** dialog, click **Set All**, and then click **API Trace**.  
  
4. In the **API Trace** dialog, click **Set All**, and then click **OK**.  
  
   When one or more trace items is enabled, the **Clear All Traces** button is enabled and tracing is started.  
  
   To stop tracing:  
  
5. In the Trace Items dialog of the **HIS Trace Utility**, click **Clear All Traces**.  
  
   When no trace items are enabled, the **Clear All Traces** button is disabled and tracing is stopped.  
  
   To view trace files:  
  
6. In the **Trace Items** dialog of the **Explore Traces**.  
  
   To purge trace files:  
  
7. In the **Trace Items** dialog of the **HIS Trace Utility**, click **Purge All Trace Files**.  
  
### Tracing Global Properties  
 The Tracing Global Properties tab has several items that can be modified to adjust how Trace runs. These items include:  
  
#### Trace File Flip Length  
 The default size is 20 Mbytes.  
  
 You can change the maximum length by highlighting the number and typing a new value.  
  
#### Stop tracing by event  
 SNA Trace can monitor the Windows Event log and stop tracing when a configured event occurs. To enable this feature, click **Monitor event log** and enter an Event ID.  
  
#### Write Traces on a Background Thread  
 Check this box to run tracing in the background. If the box is cleared (blank), tracing runs in the foreground.  
  
 To reduce performance impacts caused by tracing, traces can be queued and written by a background thread when this box is checked. Otherwise, trace files will be written immediately.  
  
#### Background Thread Priority  
 If you select **Write traces on a Background Thread**, check only one item to set the level of priority for tracing to run within the Microsoft Windows operating system. Highest gives tracing the highest level of priority, which means that tracing takes precedence over other jobs. Idle means that tracing runs when the CPU is idle.  
  
### Trace File Directory Tab  
 The **Trace File Directory** tab allows you to change where the Trace Initiator files will be stored.  
  
 Use **Browse** or enter a new location.