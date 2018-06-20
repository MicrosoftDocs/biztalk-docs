---
title: "Using Event Tracing for Windows2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ETW"
  - "Event Tracing for Windows"
ms.assetid: 88b91b74-2b2e-40e0-a3e9-1ebd6367abe8
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using Event Tracing for Windows
Microsoft BizTalk Adapter for JD Edwards OneWorld logs error, warning, and information messages to the Windows Event Viewer. You can view additional tracing messages by using the Event Tracing for Windows (ETW) tool. When ETW is activated, it creates an *.etl file to receive the messages. This file is in binary format and must be converted to be read. To do this, you must have a consumer application available to interpret the \*.etl file: for example, tracerpt.exe or tracedmp.exe.  
  
## ETW Components  
 Event Tracing for Windows has three components:  
  
- **Controller application.** Activates and deactivates a provider (for example, tracelog.exe or logman.exe).  
  
   You set your PATH environment variable to point to the location of tracelog.exe. This ensures that BTAJDEdwardsOneWorldTrace calls can locate tracelog.exe in your system. By default, BTAJDEdwardsOneWorldTrace searches the current path.  
  
  > [!NOTE]
  >  tracelog.exe is available from the Microsoft SDK and is compatible with the commands provided by BizTalk Adapter for JD Edwards OneWorld. To use logman.exe refer to the logman documentation.  
  
- **Consumer application.** Reads logged events.  
  
   For the consumer application to be able to read the event in the .etl file, Event Tracing for Windows must dump them into that file. Normally this is done when the controller deactivates the tracing.  
  
   To use the consumer application without deactivating the trace, the controller must activate the trace with the real-time option, **\<Real time\> = -rt**.  
  
- **Provider.** Provides the event.  
  
  BizTalk Adapter for JD Edwards OneWorld includes five different providers. They are registered in Windows Management Instrumentation (WMI). To find the registered providers in the root\WMI\EventTrace path, you can use tools such as WMI CIM Studio.  
  
  BizTalk Adapter for JD Edwards OneWorld has five providers, allowing you to log different kinds of messages:  
  
- **Receiver Logging Provider.** The \<Trace element\> switch is **-receiver**.  
  
- **Receiver CastDetails Provider.** The \<Trace element\> switch is **-castDetailsReceive**.  
  
- **Transmitter Logging Provider.** The \<Trace element\> switch is **-transmitter**.  
  
- **Transmitter CastDetails Provider.** The \<Trace element\> switch is **-castDetailsTransmit**.  
  
- **Management Logging Provider.** The \<Trace element\> switch is **-management**.  
  
  BTAJDEOneWorldTrace Command  
  
  To use ETW, run the BizTalk Adapter for JD Edwards OneWorld command, BTAJDEOneWorldTrace.cmd. You use this command as follows:  
  
```  
BTAJDEOneWorldTrace <Trace element> -start [-cir <MB>|   
      -seq <MB>] [-rt] logfile  
BTAJDEOneWorldTrace <Trace element> -stop  
```  
  
 Where:  
  
- **\<Trace element\>** (required) is the kind of provider.  
  
- Its options are:  
  
  -   **-castDetailsTransmit**  
  
  -   **-transmitter**  
  
  -   **-castDetailsReceive**  
  
  -   **-receiver**  
  
  -   **-management**  
  
  -   **-start, -stop**: Activate or deactivate the provider.  
  
  -   **-cir \<MB\>**: Size and kind of file. -cir is a circular file. \<MB\>: Size in meg.  
  
  -   **-seq \<MB\>**: Size and kind of file. -seq is a sequential file. \<MB\>: Size in meg.  
  
  -   **-rt**: Set the real time mode on.  
  
  -   **Logfile**: Name of the log file (c:\rtlog.etl is the default).  
  
  For example:  
  
```  
BTAJDEOneWorldTrace -transmitter -start -cir 10 -rt c:\log\mylog.etl  
BTAJDEOneWorldTrace -transmitter -stop  
```  
  
## See Also  
 [Troubleshooting JD Edwards OneWorld](../core/troubleshooting-jd-edwards-oneworld.md)