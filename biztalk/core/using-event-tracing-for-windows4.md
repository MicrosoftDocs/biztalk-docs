---
title: "Using Event Tracing for Windows4 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ETW"
  - "BTAJDEEnterpriseOneTrace command"
  - "Event Tracing for Windows"
ms.assetid: 5f07d317-5ae2-4d1e-a343-941f3079dc4b
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using Event Tracing for Windows
Microsoft BizTalk Adapter for JD Edwards EnterpriseOne logs error, warning, and information messages to the Windows Event Viewer. You can view additional tracing messages by using the Event Tracing for Windows (ETW) tool. When ETW is activated, it creates an *.etl file to receive the messages. This file is in binary format and must be converted to be read. To do this, you must have a consumer application available to interpret the \*.etl file; for example, tracerpt.exe or tracedmp.ex. The tracept.exe application converts the \*.etl into two text files: summary.txt and dumpfile.csv.  
  
## ETW Components  
 Event Tracing for Windows has three components:  
  
-   **Controller application**. Activates and deactivates a provider (for example, tracelog.exe or logman.exe).  
  
     You set your PATH environment variable to point to the location of tracelog.exe. This ensures that BTAJDEEnterpriseOneTrace calls can locate tracelog.exe in your system. By default, BTAJDEEnterpriseOneTrace searches the current path.  
  
> [!NOTE]
>  tracelog.exe is available from the Microsoft SDK and is compatible with the commands provided by  BizTalk Adapter  for JD Edwards EnterpriseOne. To use logman.exe, refer to the logman documentation.  
  
- **Consumer application**. Reads logged events. For the consumer application to be able to read the event in the etl file, Event Tracing for Windows must dump them into that file. Normally this is done when the controller deactivates the tracing.  
  
   To use the consumer application without deactivating the trace, the controller must activate the trace with the real-time option, **\<Real time\> = -rt**.  
  
- **Provider**. Used to provide the event. BizTalk Adapter for JD Edwards EnterpriseOne includes three different providers. They are registered in Windows Management Instrumentation (WMI). To find the registered providers in the root\WMI\EventTrace path, you can use tools such as WMI CIM Studio.  
  
  BizTalk Adapter  for JD Edwards EnterpriseOne contains three providers, allowing you to log different kinds of messages:  
  
- **Receiver Logging Provider**: The \<Trace element\> switch is **-receiver**. Use **-receiver** to get any messages from the log that were received by the adapter at run time.  
  
- **Transmitter Logging Provider**: The \<Trace element\> switch is **-transmitter**. Use **-transmitter** to get any messages from the log that were transmitted by the adapter at run time.  
  
- **Management Logging Provider**: The \<Trace element\> switch is **-management** Use **-management** to get any messages from the log that were generated during browsing of the server system.  
  
### BTAJDEEnterpriseOneTrace Command  
 To use ETW, run the BizTalk Adapter for JD Edwards EnterpriseOne command, **BTAJDEEnterpriseOneTrace.cmd**. You use this command as follows:  
  
```  
BTAJDEEnterpriseOneTrace <Trace element> -start [-cir <MB>|   
-seq <MB>] [-rt] logfile  
BTAJDEEnterpriseOneTrace <Trace element> -stop  
  
```  
  
 Where: **\<Trace element\>** (required) is the kind of provider.  
  
 Its options are:  
  
- **-transmitter**  
  
- **-receiver**  
  
- **-management**  
  
- **-start, -stop**: Activate or deactivate the provider.  
  
- **-cir \<MB\>**: Size and kind of file. -cir is a circular file. \<MB\>: Size in meg.  
  
- **-seq \<MB\>**: Size and kind of file. -seq is a sequential file. \<MB\>: Size in meg.  
  
- **-rt**: Set the real time mode on.  
  
- **Logfile**: Name of the log file (c:\rtlog.etl is the default).  
  
  For example:  
  
```  
BTAJDEEnterpriseOneTrace -transmitter -start -cir 10 -rt c:\log\mylog.etl  
BTAJDEEnterpriseOneTrace -transmitter -stop  
```  
  
## See Also  
 [Troubleshooting JD Edwards EnterpriseOne](../core/troubleshooting-jd-edwards-enterpriseone.md)