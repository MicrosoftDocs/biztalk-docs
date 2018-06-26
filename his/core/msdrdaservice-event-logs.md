---
title: "MsDrdaService Event Logs | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 14be169d-4355-458f-ae87-2e82373d9387
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# MsDrdaService Event Logs
The DRDA Server logs events to the Microsoft Windows application and service log named “DrdaService”. IT professionals can view this log using the Microsoft Windows Event Viewer. The DRDA Server logs events to the Event Viewer.  
  
## Event Viewer  
 The Event Viewer is a Microsoft Management Console (MMC) snap-in that enables you to browse and manage event logs. It is an indispensable tool for monitoring the health of systems and troubleshooting issues when they arise.  
  
 Event Viewer enables you to perform the following tasks:  
  
- View events from multiple event logs  
  
- Save useful event filters as custom views that can be reused  
  
- Schedule a task to run in response to an event  
  
- Create and manage event subscriptions  
  
  The Event Viewer is a Microsoft Management Console (MMC) snap-in. You can start Event Viewer by adding the snap-in to MMC or by double-clicking the snap-in file, Eventvwr.msc, which is located in the %SYSTEMROOT%\system32 folder. In addition, Event Viewer can be started from the Windows interface or the command line by using the following procedures.  
  
  To start Event Viewer by using the Windows interface:  
  
1. Click the **Start** button.  
  
2. Click **Control Panel**.  
  
3. Click **System and Maintenance**.  
  
4. Click **Administrative Tools**.  
  
5. Double-click **Event Viewer**.  
  
   To start Event Viewer by using a command line:  
  
6. Open a command prompt. To open a command prompt, click **Start**, click **All Programs**, click **Accessories** and then click **Command Prompt**.  
  
7. Type **eventvwr**.  
  
   The eventvwr.exe command-line tool supports options that determine the computer the snap-in will connect to and the event logs it will display. When connecting to a computer running a previous version of Windows, the tool can be used to start the snap-in and connect to the remote computer, but the additional command-line options are ignored.  
  
   To display additional help for the eventvwr command-line tool, type the following command at a command prompt: **eventvwr /?**.  
  
   For the latest information about Event Viewer, see Event Viewer online ([http://go.microsoft.com/fwlink/?linkid=45698](http://go.microsoft.com/fwlink/?linkid=45698)).  
  
## MsDrdaService Logs  
 The following DRDA Server events are recorded in the Microsoft Windows application and service log named “DrdaService”.  
  
|Event ID|Event Type|Event Category|Event Message Text|  
|--------------|----------------|--------------------|------------------------|  
|1011|Error|Connection|The Microsoft Service for DRDA cannot connect to SQL Server. Verify the connectionString value in the MsDrdaService.exe.config application configuration file.|  
|1012|Error|Connection|The Microsoft Service for DRDA failed to retrieve access token from ESSO server.|  
|1013|Warning|Connection|The Microsoft Service for DRDA is connecting to a remote SQL Server ({0}) database ({1}) when configured for SQL mirroring.|  
|1014|Warning|Connection|The Microsoft Service for DRDA is connecting to a local SQL Server ({0}) database ({1}) when configured for SQL mirroring.|  
|1015|Information|Connection|The Microsoft Service for DRDA TCP communication manager is listening on port {0}.|  
|1016|Information|Connection|The Microsoft Service for DRDA is operating in primary server role.|  
|1017|Information|Connection|The Microsoft Service for DRDA is operating in partner server role.|  
|1018|Information|Connection|The Microsoft Service for DRDA changed the DRDA SRVLST (Server List) values.|  
|1019|Information|Connection|The Microsoft Service for DRDA flushed package procedure cache. The Microsoft Service for DRDA flushed the package procedure cache based on the packageProcedureCacheFlush attribute value in the MsDrdaService.exe.config application configuration file.|  
|1020|Error|Connection|The Microsoft Service for DRDA cannot listen on port {0}. Verify the Port attribute value in the MsDrdaService.exe.config application configuration file.|  
|1022|Warning|Environment|The Microsoft Service for DRDA could not load a custom NLS code page file. Verify the codePage number in the codePages element of the encoding section of the MsDrdaService.exe.config application configuration file.|  
|1023|Warning|Environment|The Microsoft Service for DRDA could not load a default NLS code page file. Verify the ccsid number in the applicationEncodings element of the service section of the MsDrdaService.exe.config application configuration file.|  
|1024|Error|Extension|The Microsoft Service for DRDA cannot load a custom trace listener. Verify the attribute values in the drdaServiceTraceListeners element of the MsDrdaService.exe.config application configuration file.|  
|1025|Error|Extension|The Microsoft Service for DRDA cannot load a custom bind listener. Verify the attribute values in the packageBindListeners element of the MsDrdaService.exe.config application configuration file.|  
|1026|Error|Internal|An internal error occurred.|  
|1027|Warning|Logging|The Microsoft Service for DRDA cannot load the text trace listener. Verify the source attribute values of the sources element of the system.diagnostics section of the MsDrdaService.exe.config application configuration file.|  
|1028|Warning|Logging|The Microsoft Service for DRDA failed to write a trace log file. Verify the attribute values in the sharedListeners element of the system.diagnostics section of the MsDrdaService.exe.config application configuration file.|  
|1029|Error|Warning|The Microsoft Service for DRDA cannot create a performance counter.|  
|1030|Information|Logging|The Microsoft Service for DRDA created a trace listener instance.|  
|1031|Warning|Logging|The Microsoft Service for DRDA did not find trace log file in the configured directory. The Microsoft Service for DRDA will create a new trace log file in the default location. Verify the source traceFileFolder value of the sharedListeners element of the system.diagnostics section of the MsDrdaService.exe.config application configuration file.|  
|1032|Information|Logging|The Microsoft Service for DRDA trace file contains the maximum allowed number of trace entries. Verify the maxTraceEntries attribute value of the sharedListeners element of the system.diagnostics section of the MsDrdaService.exe.config application configuration file.|  
|1033|Error|Management|The Microsoft Service for DRDA cannot find the configuration file. Verify that the Microsoft Service for DRDA MsDrdaService.exe.config application configuration file is in the default system directory.|  
|1034|Error|Management|The Microsoft Service for DRDA failed to load the configuration file. Verify the format of the Microsoft Service for DRDA XML MsDrdaService.exe.config application configuration file.|  
|1035|Information|Management|The Microsoft Service for DRDA has re-read a modified MsDrdaService.exe.config application configuration file.|  
|1036|Warning|Security|The Microsoft Service for DRDA has detected a possible denial of service attack. The Microsoft Service for DRDA rejected DRDA client requests from TCP/IP address not configured in the clientIpAddressesAllowed attribute of the configuration file.|  
|1037|Warning|Startup/Shutdown|The Microsoft Service for DRDA has stopped.|  
|1038|Error|Startup/Shutdown|The Microsoft Service for DRDA cannot start.|  
|1039|Error|Startup/Shutdown|The Microsoft Service for DRDA cannot stop.|  
|1040|Information|Startup/Shutdown|The Microsoft Service for DRDA (Build: 9.0.1789.0) started.|  
|1042|Information|Startup/Shutdown|The Microsoft Service for DRDA processed the package procedure last invoke list. The Microsoft Service for DRDA processed the package procedures listed in the packageProcedureLastInvoke attribute value of the MsDrdaService.exe.config application configuration file.|  
|1043|Warning|Trace/Log|The Microsoft Service for DRDA failed to create specified trace directory {0}. Using the default trace directory.|  
|1044|Error|Trace/Log|The Microsoft Service for DRDA failed to created trace file {0}. Exception message: {1}|  
|1056|Error|Connection|The Microsoft Service for DRDA failed to load error mappings Xml. Error message: {0}|  
|1057|Error|Connection|The Microsoft Service for DRDA failed to load event mappings Xml. Error message: {0}|  
|1058|Error|Connection|The Microsoft Service for DRDA failed to load DB2 to SQL data mappings Xml. Error message: {0}|  
|1059|Error|Connection|The Microsoft Service for DRDA failed to load SQL to DB2 data mappings Xml. Error message: {0}|  
  
 *DRDA Server events logged to Windows event log.*