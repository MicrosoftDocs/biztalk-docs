---
redirect_url: /biztalk/core/troubleshooting-tibco-rendezvous/
redirect_document_id: TRUE

ROBOTS: NOINDEX
--- 

# Using Event Tracing for Windows
Microsoft BizTalk Adapter for TIBCO Rendezvous logs error, warning, and information messages to the Windows Event Viewer. You can see additional tracing messages by using the Event Tracing for Windows (ETW) tool. When ETW is activated, it creates an *.etl file to receive the messages. This file is in binary format and must be converted to be read. To do this, you must have a consumer application available to interpret the \*.etl file, for example, tracerpt.exe or tracedmp.exe. For example, the tracerpt.exe application will convert the \*.etl file into two text files: summary.txt and dumpfile.csv.  
  
## ETW Components  
 Event Tracing for Windows has three components:  
  
-   **Controller application**: Activates and deactivates a provider (for example, tracelog.exe or logman.exe).  
  
     You set your PATH environment variable to point to the location of tracelog.exe. This makes sure that BTATIBCO RendezvousTrace calls can locate tracelog.exe in the system. By default, BTATIBCO RendezvousTrace searches the current path.  
  
> [!NOTE]
>  tracelog.exe is available from the Microsoft SDK and is compatible with the commands provided by Microsoft BizTalk Adapter for TIBCO Rendezvous. To use logman.exe, see the logman documentation.  
  
- **Consumer application**: Reads logged events.  
  
   For the consumer application to be able to read the event in the etl file, Event Tracing for Windows must dump them into that file. Typically this is done when the controller deactivates the tracing.  
  
   To use the consumer application without deactivating the trace, the controller must activate the trace with the real time option, \<Real time\> = -rt.  
  
- **Provider**: Provides the event.  
  
   BizTalk Adapter for TIBCO Rendezvous includes three different providers. They are registered in Windows Management Instrumentation (WMI). To find the registered providers in the root\WMI\EventTrace path, you can use tools such as WMI CIM Studio.  
  
  BizTalk Adapter for TIBCO Rendezvous has three providers. This lets you log different kinds of messages:  
  
- **Receiver Logging Provider**: The \<Trace element\> switch is **-receiver**.  
  
- Use **-receiver** to get any messages from the log that were received by the adapter at runtime.  
  
- **Transmitter Logging Provider**: the \<Trace element\> switch is **-transmitter**.  
  
   Use **-transmitter** to get any messages from the log that were transmitted by the adapter at run time.  
  
- <strong>Management Logging Provider—</strong>the \<Trace element\> switch is **-management**.  
  
   Use **-management**to get any messages from the log that were generated during browsing of the server system.  
  
## BTATIBCORVTrace Command  
 To use ETW, run the BizTalk Adapter for TIBCO Rendezvous command, BTATIBCORVTrace.cmd. You use this command as follows:  
  
```  
BTATIBCORVTrace <Trace element> -start [-cir <MB>|   
-seq <MB>] [-rt] logfile  
BTATIBCORVTrace <Trace element> -stop  
```  
  
 Where: **\<Trace element\>** (required) is the kind of provider.  
  
 Its options are as follows:  
  
- **-transmitter**  
  
- **-receiver**  
  
- **-management**  
  
- **-start, -stop**: Activate or deactivate the provider.  
  
- **-cir \<MB\>**: Size and kind of file. **-cir** is a circular file. **\<MB\>**: Size in megabytes.  
  
- **-seq \<MB\>**: Size and kind of file. **-seq** is a sequential file. **\<MB\>**: Size in megabytes.  
  
- **-rt**: Set the real time mode on.  
  
- **Logfile**: Name of the log file (c:\rtlog.etl is the default).  
  
  For example:  
  
```  
BTATIBCORVTrace -transmitter -start -cir 10 -rt c:\log\mylog.etl  
BTATIBCORVTrace -transmitter -stop  
```  
  
## See Also  
 [Troubleshooting TIBCO Rendezvous](../core/troubleshooting-tibco-rendezvous.md)