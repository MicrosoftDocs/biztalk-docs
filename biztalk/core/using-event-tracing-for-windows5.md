---
title: "Using Event Tracing for Windows5 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ETW"
  - "events, Event Tracing for Windows"
  - "controller application"
  - "ETW components"
  - "consumer application"
  - "Provider"
  - "Event Tracing for Windows"
  - "Event Tracing for Windows, components"
  - "BTAPeopleSoftTrace command"
ms.assetid: 330ef84b-5e2a-4b79-85a9-72271eb489d2
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using Event Tracing for Windows
Microsoft BizTalk Adapter for PeopleSoft Enterprise logs error, warning, and information messages to the Windows Event Viewer. You can see additional tracing messages by using the Event Tracing for Windows (ETW) tool. When ETW is enabled, it creates an *.etl file to receive the messages. The file is in binary format and must be converted to be read. To do this you must have a consumer application available to interpret the \*.etl file; for example, tracerpt.exe or tracedmp.exe.  
  
## ETW Components  
 Event Tracing for Windows has three components:  
  
- **Controller application**: Activates and deactivates a provider (for example, tracelog.exe or logman.exe).  
  
   You set your PATH environment variable to point to the location of tracelog.exe. This makes sure that `BTAPeopleSoftTrace` calls can locate tracelog.exe in the system. By default, BTAPeopleSoftTrace searches the current path.  
  
  > [!NOTE]
  >  tracelog.exe is available from the Microsoft SDK and is compatible with the commands provided by BizTalk Adapter for PeopleSoft Enterprise. To use logman.exe, see the logman documentation.  
  
- **Consumer application**: Reads logged events.  
  
   For the consumer application to be able to read the event in the .etl file, Event Tracing for Windows must dump them into that file. Typically this is done when the controller deactivates the tracing.  
  
   To use the consumer without deactivating the trace, the controller must activate the trace with the real time option, \<Real time\> = -rt.  
  
- **Provider:** Provides the event.  
  
   BizTalk Adapter for PeopleSoft Enterprise has five different providers. They are registered in Windows Management Instrumentation (WMI). To find the registered providers in the **root\WMI\EventTrace** path, you can use tools such as WMI CIM Studio.  
  
  BizTalk Adapter for PeopleSoft Enterprise has five providers, allowing you to log different kinds of messages:  
  
- **Receiver Logging Provider**: The \<Trace element\> switch is **-receiver**.  
  
- **Receiver CastDetails Provider**: The \<Trace element\> switch is **-castDetailsReceive**.  
  
- **Transmitter Logging Provider**: The \<Trace element\> switch is **-transmitter**.  
  
- **Transmitter CastDetails Provider**: The \<Trace element\> switch is **-castDetailsTransmit**.  
  
- **Management Logging Provider**: The \<Trace element\> switch is **-management**.  
  
## BTAPeopleSoftTrace Command  
 To use ETW, run the adapter command, **BTAPeopleSoftTrace.cmd**. You use this command as follows:  
  
```  
BTAPeopleSoftTrace <Trace element> -start [-cir <MB>|   
    -seq <MB>] [-rt] logfile  
BTAPeopleSoftTrace <Trace element> -stop  
```  
  
 Where:  
  
- \<Trace element\> (required) is the kind of provider.  
  
   Options are as follows:  
  
  -   **-castDetailsTransmit**  
  
  -   **-transmitter**  
  
  -   **-castDetailsReceive**  
  
  -   **-receiver**  
  
  -   **-management**  
  
  -   **-start, -stop**: Activate or deactivate the provider.  
  
- **-cir \<MB\>**: Size and kind of file. -cir is a circular file. \<MB\>: Size in megabytes.  
  
- **-seq \<MB\>**: Size and kind of file. -seq is a sequential file. \<MB\>: Size in megabytes.  
  
- **-rt**: Set the real time mode on.  
  
- **Logfile**: Name of the log file (C:\rtlog.etl is the default).  
  
  For example:  
  
```  
BTAPeopleSoftTrace -transmitter -start -cir 10 -rt C:\log\mylog.etl  
BTAPeopleSoftTrace -transmitter -stop  
```  
  
## See Also  
 [Troubleshooting PeopleSoft](../core/troubleshooting-peoplesoft.md)