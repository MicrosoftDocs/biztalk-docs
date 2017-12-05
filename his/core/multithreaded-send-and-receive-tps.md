---
title: "Multithreaded Send and Receive TPs | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 46d584d3-ec36-482c-b2cc-700ff9eccde6
caps.latest.revision: 4
---
# Multithreaded Send and Receive TPs
These multithreaded send and receive TPs are more advanced than the single-threaded equivalents. The samples located in the MSENDRCV subdirectory all use the asynchronous interface of APPC, with verb completion signaled by events ([WinAsyncAPPCEx](../core/winasyncappcex2.md)) or IO completion ports ([WinAsyncAPPCIOCP](../core/winasyncappciocp1.md)). These TPs show how to code multithreaded APPC applications with multiple conversations per thread. They are more complex than the single-threaded equivalents, but are also more realistic.  
  
 If you are unfamiliar with APPC, examine the single-threaded TPs first. If you are unfamiliar with methods of creating threads or processing events in Microsoft Windows, see the Microsoft Platform SDK documentation along with the multithreaded TPs.  
  
 **Setup**  
  
 There are four multithreaded send and receive routines that illustrate using asynchronous APPC calls:  
  
-   MRCV for receiving using events for notification  
  
-   MRCVIO for receiving using IO completion ports for notification  
  
-   MSEND for sending using events for notification  
  
-   MSENDRCV for simultaneous sending and receiving using events for notification  
  
 To set up these TPs, create an appropriate APPC LU-LU-mode triplet. The default is SENDLU-RECVLU-#INTER, but this can be configured (see the sections that follow). To run a large number of simultaneous conversations, increase the session limits for #INTER or use another mode with large session limits.  
  
 One obvious way of configuring these programs is to configure MSEND to run with MRCV or MRCVIO; another way is to configure MSENDRCV to run with another copy of MSENDRCV. However, you can also configure MSEND to run with one or more copies of RECVTP (the single-threaded version) and MRCV or MRCVIO to run with one or more copies of SENDTP. You can also configure MSENDRCV to run with MSEND, MRCV, SENDTP or RECVTP. For more information, see the sections that follow.  
  
 One possible arrangement is to place SENDTP (single-threaded) on multiple client computers, and configure MRCV or MRCVIO (multithreaded) on a server so that it interacts with all the TPs on the clients. Many other arrangements are possible.  
  
 **Configuration for MRCV, MSEND, and MSENDRCV**  
  
 The MRCV, MSEND, and MSENDRCV TP samples use a configuration file for configuration and input. To name the file, use .CFG as the extension, and use the same base file name and directory location as the executable file (the TP itself).  
  
 The following table shows examples of CFG files that could be used with MSEND and MRCV.  
  
|Example of MSEND.CFG file|Example of MRCV.CFG file|  
|-------------------------------|------------------------------|  
|ResultFile=MSEND.OUT|TraceFile=MRCV.TRC|  
|TraceFile=MSEND.TRC|LocalTPName=MRCVTP|  
|RemoteTPName=MRCVTP|NumRcvConvs=32|  
|LocalLUAlias=LUA|NumRcvThreads=4|  
|RemoteLUAlias=LUB|RcvSize=4096|  
|ModeName=#INTER||  
|NumSendConvs=32||  
|NumSends=128||  
|ConfirmEvery=16||  
|SendSize=256||  
  
 For MSEND, the configuration file (MSEND.CFG) can contain the following items, one per line, in any order. If a variable is not found in the file or the file is not present, the default is used.  
  
|Line|Default value|Value to supply|  
|----------|-------------------|---------------------|  
|ResultFile =|MSEND.OUT|File name to print timings to (located in default directory for MSEND)|  
|TraceFile =|MSEND.TRC|Trace file name (located in default directory for MSEND)|  
|LocalLUAlias =|SENDLU|Local LU alias|  
|RemoteLUAlias =|RECVLU|Remote LU alias|  
|ModeName =|#INTER|Mode name|  
|RemoteTPName =|MRCVTP|Name of remote TP (for [MC_ALLOCATE](../core/mc-allocate1.md))|  
|NumSendConvs =|4|Number of conversations to send|  
|NumSends =|8|Number of [MC_SEND_DATA](../core/mc-send-data2.md) verbs per conversation|  
|SendSize =|256|Size in bytes of data sent each time|  
|ConfirmEvery =|2|Number of **MC_SEND_DATA** verbs between [MC_CONFIRM](../core/mc-confirm1.md) verbs|  
  
 The following lines are for MRCV:  
  
|Line|Default value|Value to supply|  
|----------|-------------------|---------------------|  
|TraceFile =|MRCV.TRC|Trace file name (located in default directory for MSEND)|  
|LocalTPName =|MRCVTP|Name of local TP (for [RECEIVE_ALLOCATE](../core/receive-allocate2.md))|  
|NumRcvConvs =|4|Number of conversations to receive|  
|NumRcvThreads =|2|Number of threads to start for processing receive conversations|  
|RcvSize =|4096|Size in bytes of receive buffer for [MC_RECEIVE_AND_WAIT](../core/mc-receive-and-wait1.md)|  
  
 The following table shows examples of configuration files (MSENDRCV.CFG) that could be used with MSENDRCV. Each row of the table (Example A and Example B) contains two files that work together on a pair of computers.  
  
|Example A of MSENDRCV.CFG|Example B of MSENDRCV.CFG|  
|-------------------------------|-------------------------------|  
|ResultFile=MSENDRCV.OUT|ResultFile=MSENDRCV.OUT|  
|TraceFile=MSENDRCV.TRC|TraceFile=MSENDRCV.TRC|  
|LocalTPName=TPA|LocalTPName=TPB|  
|RemoteTPName=TPB|RemoteTPName=TPA|  
|LocalLUAlias=LUA|LocalLUAlias=LUB|  
|RemoteLUAlias=LUB|RemoteLUAlias=LUA|  
|ModeName=#INTER|ModeName=#INTER|  
|NumRcvConvs=50|NumRcvConvs=25|  
|NumRcvThreads=4|NumRcvThreads=4|  
|RcvSize=4096|RcvSize=4096|  
|NumSendConvs=25|NumSendConvs=50|  
|NumSends=100|NumSends=100|  
|ConfirmEvery=10|ConfirmEvery=10|  
|SendSize=256|SendSize=256|  
  
 The following lines are for MSENDRCV:  
  
|Line|Default value|Value to supply|  
|----------|-------------------|---------------------|  
|ResultFile =|MSENDRCV.OUT|File name to print timings to (located in default directory for the MSEND or MSENDRCV sending TP)|  
|TraceFile =|MSENDRCV.TRC|Trace file name (located in default directory for the MSEND or MSENDRCV sending TP)|  
|LocalLUAlias =|SENDLU|Local LU alias|  
|RemoteLUAlias =|RECVLU|Remote LU alias|  
|ModeName =|#INTER|Mode name|  
|RemoteTPName =|MRCVTP|Name of remote TP (for [MC_ALLOCATE](../core/mc-allocate1.md))|  
|NumSendConvs =|4|Number of conversations to send|  
|NumSends =|8|Number of [MC_SEND_DATA](../core/mc-send-data2.md) verbs per conversation|  
|SendSize =|256|Size in bytes of data sent each time|  
|ConfirmEvery =|2|Number of **MC_SEND_DATA** verbs between [MC_CONFIRM](../core/mc-confirm1.md) verbs|  
|LocalTPName =|MRCVTP|Name of local TP (for [RECEIVE_ALLOCATE](../core/receive-allocate2.md))|  
|NumRcvConvs =|4|Number of conversations to receive|  
|NumRcvThreads =|2|Number of threads to start for processing receive conversations|  
|RcvSize =|4096|Size in bytes of receive buffer for [MC_RECEIVE_AND_WAIT](../core/mc-receive-and-wait1.md)|  
  
 The output from MSEND and MSENDRCV consists of details of the configuration and the time taken for each conversation, and is sent to the result file specified in MSEND.CFG or MSENDRCV.CFG.  
  
 **Operation of MRCV, MSEND, and MSENDRCV**  
  
 The MRCV, MSEND, and MSENDRCV TPs use multiple event processing in Windows to avoid creating an unnecessary number of threads.  
  
 These TPs also use Windows-based processing, but this is incidental. Its only purpose is to display beneath the icon on the screen a running count of threads, the number of conversations currently sending or receiving data, and the number of conversations completed. The Windows-based processing could easily be removed to create a completely batch-oriented program. To do this, termination would need to be signaled with an event rather than with WM_CLOSE.  
  
 The TP name used in [TP_STARTED](../core/tp-started1.md) is the name of the executable file (MSEND, MRCV, or MSENDRCV). The TP names used in [MC_ALLOCATE](../core/mc-allocate1.md) and [RECEIVE_ALLOCATE](../core/receive-allocate2.md) can be configured, as shown in the preceding tables.  
  
 MSEND reads its configuration file (or uses defaults) to determine the number of send conversations to start. Each conversation reads the value of **NumSends** (or uses the default), issues that number of [MC_SEND_DATA](../core/mc-send-data2.md) verbs, and then terminates. When all of the conversations for a thread have terminated, the thread itself terminates. When all of the send threads have terminated, the program terminates.  
  
 An [MC_CONFIRM](../core/mc-confirm1.md) verb is issued before the first **MC_SEND_DATA** and then at the intervals specified by **ConfirmEvery**. The complete data flow for a conversation is as follows:  
  
 **TP_STARTED**  
  
 **MC_ALLOCATE**  
  
 **MC_CONFIRM**  
  
 **MC_SEND_DATA** (repeated the number of times specified by **ConfirmEvery**)  
  
 **MC_CONFIRM**  
  
 **MC_SEND_DATA** (repeated the number of times specified by **ConfirmEvery**)  
  
 **MC_CONFIRM**  
  
 (Pattern repeats until the number of **MC_SEND_DATA** verbs equals **NumSends**.)  
  
 **MC_DEALLOCATE**  
  
 **TP_ENDED**  
  
 MRCV starts up an initial thread for issuing [RECEIVE_ALLOCATE](../core/receive-allocate2.md) verbs, and then reads its configuration file (or uses defaults) to determine the number of receive threads to start and the number of conversations to receive. The initial thread issues a **RECEIVE_ALLOCATE** and waits. When the **RECEIVE_ALLOCATE** completes, the initial thread turns the processing of the conversation over to the next available receive thread, and issues another **RECEIVE_ALLOCATE**. This process continues until the configured number of **RECEIVE_ALLOCATE** verbs (that is, **NumRcvConvs**) have completed.  
  
 There is a limit to the number of conversations that can be supported on a thread, because of the limit to the number of events that can be waited for with **WaitForMultipleObjects** (a function in the Win32® API). For send threads, the limit is 64 conversations per thread; for receive threads, the limit is 63 conversations per thread.  
  
 MSEND works with this limit by starting enough threads to support the configured number of conversations. For example, if **NumSendConvs** is set to 200, four send threads are started: three of them process 64 conversations each and one processes the remaining eight conversations.  
  
 MRCV works with this limit by comparing **NumRcvConvs** to **NumRcvThreads**. If **NumRcvConvs** is more than (63 \* **NumRcvThreads**), **NumRcvThreads** is increased. If **NumRcvThreads** is greater than **NumRcvConvs**, **NumRcvThreads** is reduced to prevent creating unneeded threads.  
  
 With MRCV, to ensure that a receive thread correctly picks up the conversation, two special events are used per thread: *event1* and *event2*. The following table illustrates their use.  
  
|RECEIVE_ALLOCATE thread|Receive thread|  
|------------------------------|--------------------|  
|Issue [RECEIVE_ALLOCATE](../core/receive-allocate2.md) and wait|Wait for *event1*|  
|(**RECEIVE_ALLOCATE** completes)||  
|Select next receive thread and  set *event1* for that thread; then wait for *event2* for that thread||  
||(*Event1* completes)|  
||Add conversation to list of conversations being processed|  
||Set *event2*|  
|(*Event2* completes)||  
|REPEAT|REPEAT|  
  
 The receive thread waits not only on the *event1* set for it, but also on one event for each conversation the thread is processing.  
  
 If **NumRcvConvs** is set to zero, the **RECEIVE_ALLOCATE** thread will never terminate. If **NumSends** is set to zero, the conversation will never terminate; this is useful for getting the maximum number of simultaneous conversations.  
  
 **Tracing of MRCV, MSEND, and MSENDRCV**  
  
 If you want to observe the detailed processing of the MRCV, MSEND, or MSENDRCV sample TPs, you can enable tracing. To do this, find the following line, commented out, near the top of the file:  
  
```  
#define SRTRC  
```  
  
 Enable this line or define this value on the command-line option to the compiler, and trace statements will be written to the trace file(s) specified by the **TraceFile** variable in the configuration.  
  
 There are also some trace statements that have been commented out. If they are left commented out, only [MC_CONFIRM](../core/mc-confirm1.md) and [MC_CONFIRMED](../core/mc-confirmed2.md) processing is traced while a conversation is running, to maintain a send or receive count without generating a large amount of trace information. You can activate the detailed tracing of events (such as the sending of data) by enabling one or more trace statements.  
  
 The Trace Initiator (snatrace.exe) tool provides APPC API tracing for Microsoft Host Integration Server applications. For more information about the Trace Initiator and Trace Viewer tools, see Microsoft Host Integration Server Help.  
  
 **Configuration for MRCVIO**  
  
 The MRCVIO TP sample is a multithreaded console application that uses command-line options for configuration and input. If an option is not provided on the command line, then the default is used. The following table lists the possible command-line options for MRCVIO.  
  
|Command-line option|Description|  
|--------------------------|-----------------|  
|-?|Displays usage information for this sample and exits.|  
|-c numRcvConvs|The maximum number of APPC conversations to support.<br /><br /> The default value is 8 with a maximum value of 64.|  
|-d duration|The number of seconds that the sample application should run. The default value is 60 seconds.<br /><br /> A value of 0 for duration means run indefinitely.|  
|-h|Displays usage information for this sample and exits.|  
|-i IntTraceFile|The name of the internal trace file if tracing is required. When this command-line option is specified, internal tracing is enabled.<br /><br /> This option has no default value and internal tracing is turned off.|  
|-n numRcvThreads|The number of Completion Port threads to allocate.<br /><br /> The default value is 4 with a maximum value of 32.|  
|-r rcvSize|The size in bytes of the buffer supplied on each **RECEIVE_ALLOCATE**.<br /><br /> The default value is 4096 with a maximum value of 65535.|  
|-t TPName|The name supplied on the **RECEIVE_ALLOCATE** verbs.<br /><br /> The default value is the "MRCVTP" string.|  
  
## Operation of MRCVIO  
 The MRCVIO TP sample uses IO completion ports for notification and will only operate on Windows. Using the IO completion port mechanism is the preferable method for writing scalable APPC server applications.  
  
 The MRCVIO TP sample contains the routines for a multithreaded console application that uses asynchronous APPC calls on a single I/O completion port to receive data. The MRCVIO sample creates a small pool of threads that will be used for processing RECEIVE requests. It operates in conjunction with one of the following:  
  
-   Single-threaded version of send(SENDTP)  
  
-   Multithreaded event-based versions of send (MSEND, MSENDRCV)  
  
 The MRCVIO sample uses a server model that continues to accept conversations via [RECEIVE_ALLOCATE](../core/receive-allocate2.md) until the application is manually terminated, or a specified timer expires. The conversations do not belong to any particular RECEIVE thread. Each receive thread issues **GetQueuedCompletionStatus** calls to wait for completion of an APPC verb (on any conversation). Each conversation issues **MC_RECEIVE_AND_WAIT** verbs to receive data. If confirmation is requested, an **MC_CONFIRM** verb is issued.  
  
 The TP name used in [MC_ALLOCATE](../core/mc-allocate1.md) and [RECEIVE_ALLOCATE](../core/receive-allocate2.md) can be configured by using the command-line options as shown in the preceding table of options for the configuration of MRCVIO.  
  
 MRCVIO starts up and parses its command-line options (or uses defaults) to determine the number of receive threads to start, the number of conversations to receive, the buffer size for each **RECEIVE_ALLOCATE**, its TP name, how long the application should run, and whether internal tracing is enabled.  
  
 Once command-line options are parsed, the MRCVIO sample calls the **CreateCompletionPort** function to allocate the IO completion port. If this call is successful, then the specified number of threads are created with the thread start routine pointing to the MRCVIO **ReceiveThread** function and the thread priority for each thread is lowered. Then the specified number of APPC conversations are started.  
  
 The MRCVIO sample uses the IO completion port structure and the [WinAsyncAPPCIOCP](../core/winasyncappciocp1.md) function as listed below.  
  
```  
/* IOCP - Structure and function prototype          */  
typedef struct  
{  
    HANDLE       APPC_CompletionPort;  
    DWORD        APPC_NumberOfBytesTransferred;  
    DWORD        APPC_CompletionKey;  
    LPOVERLAPPED APPC_pOverlapped;  
} APPC_IOCP_INFO;  
extern HANDLE WINAPI WinAsyncAPPCIOCP(  
    APPC_IOCP_INFO* iocp_handle, // IO completion port information  
    long lpVcb);                 // pointer to APPC verb control block  
```  
  
 The APPC_CompletionPort must be a HANDLE returned by the **CreateIoCompletionPort** function issued by the application before using **WinAsyncAPPCIOCP**. The other three fields can be set to any value whatsoever. The APPC library does nothing with these other fields, except to return them unaltered on the **GetQueuedCompletionStatus** when the APPC verb completes. Application developers can set these values to whatever they like, but assuming the server application is handling multiple concurrent APPC conversations, an application will need to use one of these three fields to correlate APPC verbs with their completions.  
  
 For example, the MRCVIO sample passes a pointer to a Conversation Control Block into the APPC_pOverlapped field when it issues an APPC verb. The same value is returned when the APPC verb completes on the **GetQueuedCompletionStatus**. This allows the sample MRCVIO TP to figure out which APPC verb has actually completed. APPC developers can use a different method (an index into an array of VCBs, for example) to provide the same effect.  
  
 Also, an application might use the APPC_CompletionKey field to distinguish between APPC events and other events posted to this IO Completion port. For example, the MRCVIO sample sets this value to a user-defined constant IOCP_VERB_COMPLETE so that the **GetQueuedCompletionStatus** function can distinguish APPC verb completions from the other events that are posted to this IO Completion port (IOCP_START_CONVERSATION, IOCP_END_CONVERSATION and IOCP_TERMINATE_THREAD). However, this is purely for the convenience of the application. An APPC developer could decide not to post any events to its IO Completion port (except implicitly for APPC completions). In such a case, it would be unnecessary to set any value in the APPC_CompletionKey.  
  
## See Also  
 [APPC Samples](../core/appc-samples.md)