---
title: "APPC Send and Receive TPs | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9de62f86-ad2e-49e5-9265-6ad45540ba2c
caps.latest.revision: 4
---
# APPC Send and Receive TPs
These are simple APPC send and receive TPs that illustrate the use of asynchronous verb completion. This sample implements simple bulk data sending and receiving TPs (SENDTP and RECVTP).  
  
 **Setup**  
  
 To set up these TPs, create an appropriate APPC LU-LU-mode triplet. The default is SENDLU-RECVLU-#INTER, but this can be configured (see the following sections).  
  
 **Input and Output**  
  
 The APPC send and receive TPs each use a configuration file for input. To name the file, use .CFG as the extension, and use the same base file name as the TP executable file (SENDTP.CFG, for example). Save this configuration file in the same directory location as the executable file (the TP itself).  
  
 For SENDTP, the configuration file (called SENDTP.CFG if the executable file is SENDTP.EXE) can contain the following items, one per line, in any order. If a variable is not found in the file or the file is not present at all, the default is used.  
  
|Line|Default value|Value to supply|  
|----------|-------------------|---------------------|  
|ResultFile =|C:\SENDTP.OUT|File name to print timings to|  
|LocalLUAlias =|SENDLU|Local LU alias|  
|RemoteLUAlias =|RECVLU|Remote LU alias|  
|ModeName =|#INTER|Mode name|  
|LocalTPName =|SENDTP|Name of local TP|  
|RemoteTPName =|RECVTP|Name of remote TP|  
|NumConversations =|1|Number of conversations|  
|NumSends =|2|Number of [SEND_DATA](../HIS2010/send-data2.md) verbs per conversation|  
|SendSize =|1024|Size in bytes of data sent each time|  
|ConfirmEvery =|1|Number of **SEND_DATA** verbs between [CONFIRM](../HIS2010/confirm1.md) verbs|  
|SendConversation =|No|Yes or No: Use the [SEND_CONVERSATION](../HIS2010/send-conversation1.md) verb rather than the sequence of [ALLOCATE](../HIS2010/allocate1.md), **SEND_DATA**, [DEALLOCATE](../HIS2010/deallocate1.md)|  
  
 RECVTP uses a RECVTP.CFG file in a similar way, but only to read the **LocalTPName** field.  
  
 The output from SENDTP and RECVTP consists of details of the configuration and the time taken for each conversation, and is sent to the result file specified in SENDTP.CFG.  
  
## Operation  
 RECVTP should be started first; it issues [RECEIVE_ALLOCATE](../HIS2010/receive-allocate2.md) with the specified TP name. SENDTP is then started; it first issues [MC_SEND_CONVERSATION](../HIS2010/mc-send-conversation2.md) to tell RECVTP how many conversations will be carried out. It then carries out the specified number of conversations.  
  
 For SENDTP, each conversation consists of an [MC_ALLOCATE](../HIS2010/mc-allocate1.md) verb, followed by a given number of [MC_SEND_DATA](../HIS2010/mc-send-data2.md) verbs of a given size, and interspersed with [MC_CONFIRM](../HIS2010/mc-confirm1.md) verbs at a given interval, followed by an [MC_DEALLOCATE](../HIS2010/mc-deallocate1.md).  
  
 RECVTP issues [MC_RECEIVE_AND_WAIT](../HIS2010/mc-receive-and-wait1.md) when **RECEIVE_ALLOCATE** completes, and then issues either [MC_RECEIVE_AND_WAIT](../HIS2010/mc-receive-and-wait1.md) or [MC_CONFIRMED](../HIS2010/mc-confirmed2.md) according to the return from the previous **MC_RECEIVE_AND_WAIT**.  
  
 At any stage, if the TPs encounter an error, they terminate. Use APPC API tracing to diagnose problems with the configuration.  
  
 At the end of the specified number of conversations, SENDTP sends timing information to a file.  
  
 Both TPs are built from a single source code file, SENDRECV.C. SENDTP is compiled only if **-DSENDTP** is used on the command line.  
  
 The TPs run as Windows applications with a minimized window, the title bar of which displays the status. When the WndProc of this window, TPWndProc, receives the WM_CREATE message for the window, this triggers the issuing of the first verb. When TPWndProc receives an ASYNC_COMPLETE message from Windows APPC, this triggers the issuing of the next verb, dependent on what the previous verb was. When the window is closed, [WinAPPCCleanup](../HIS2010/winappccleanup2.md) is issued to terminate any active conversations.  
  
## See Also  
 [APPC Samples](../HIS2010/appc-samples.md)