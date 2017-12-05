---
title: "CPI-C Send and Receive TPs | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fd0b7eea-96b0-45a9-bdac-a7701af85c99
caps.latest.revision: 4
---
# CPI-C Send and Receive TPs
These transaction programs (TPs) are Common Programming Interface for Communications (CPI-C) versions of the APPC send and receive TPs. The sample code illustrates the use of asynchronous CPI-C calls.  
  
## Setup  
 In order to use these TPs, follow these steps:  
  
#### To set up the send and receive TPs  
  
1.  Create an appropriate APPC LU-LU-mode triplet.  
  
2.  Set up a CPI-C symbolic destination name that contains the configured remote LU and mode. (The default symbolic destination name is CPICRECV.)  
  
3.  Assign the local APPC LU to the CPICSEND TP, either by using a registry entry of CPICSEND:REG_SZ:*LocalLUAlias* in the **SnaBase\Parameters\Clients** key, or by assigning the local LU as the default local APPC LU for the user who will run CPICSEND.  
  
 For example, use SENDLU-RECVLU-#INTER as your LU-LU-mode triplet. Then, create a CPI-C symbolic destination name CPICRECV containing the application TP name CPICRECV, the partner LU alias RECVLU, and the mode name #INTER. Finally, add the intended user to the users list, and assign SENDLU as the users default local APPC LU.  
  
## Input and Output  
 CPICSEND and CPICRECV use the files Cpicsend.cfg and Cpicrecv.cfg for input. These files should be placed in the folder that contains the TP executable file. These files are similar to the input files for the APPC send and receive TPs.  
  
 The following entries are for CPICSEND only:  
  
|Line|Default Value|Description|  
|----------|-------------------|-----------------|  
|ResultFile =|C:\Cpicsend.out|The file name where the timings results will be stored.|  
|NumSends =|2|The number of [Send_Data](../core/send-data-cpi-c-1.md) calls per conversation.|  
|SendSize =|1024|The size of data sent each time in bytes .|  
|ConfirmEvery =|1|The number of **Send_Data** calls between [Confirm](../core/confirm-cpi-c-1.md) calls. If ConfirmEvery=0, CPICSEND will not issue CONFIRM verbs.|  
|SymDestName =|CPICRECV|The symbolic destination name.|  
|NumConversations =|1|The number of conversations. This setting must be the same for CPICSEND and CPICRECV. (They do not negotiate the number.) If this value is zero, the TPs will do an infinite number of conversations.|  
|WaitMode=|No|Yes, No, or Block.<br /><br /> If WaitMode=No, the verbs are completed through posted windows messages. The TPs issue [Specify_Windows_Handle](../core/specify-windows-handle-cpi-c-1.md) with a window handle so that Windows CPI-C will post completion messages to this window handle.<br /><br /> If WaitMode=Yes, verbs are non-blocking and completed using asynchronous call completion. In this case, the TPs issue **Specify_Windows_Handle** with NULL so that the TPs must then issue a [Wait_For_Conversation](../core/wait-for-conversation-cpi-c-2.md) call to wait for the asynchronous call to complete.<br /><br /> If WaitMode=Block, all verbs are blocking.|  
  
 The following entries are for CPICRECV only:  
  
|Line|Default value|Description|  
|----------|-------------------|-----------------|  
|ResultFile =|C:\Cpicrecv.out|The file name where the timings results will be stored.|  
|LocalTPName =|CPICRECV|The local TP name to use on the [Specify_Local_TP_Name](../core/specify-local-tp-name-cpi-c-1.md) call.|  
|NumConversations =|1|The number of conversations. This setting must be the same for CPICSEND and CPICRECV. (They do not negotiate the number.) If this value is zero, the TPs will do an infinite number of conversations.|  
|WaitMode=|No|Yes, No, or Block.<br /><br /> If WaitMode=No, the verbs are completed through posted windows messages. The TPs issue [Specify_Windows_Handle](../core/specify-windows-handle-cpi-c-1.md) with a window handle so that Windows CPI-C will post completion messages to this window handle.<br /><br /> If WaitMode=Yes, verbs are non-blocking and completed using asynchronous call completion. In this case, the TPs issue **Specify_Windows_Handle** with NULL so that the TPs must then issue a [Wait_For_Conversation](../core/wait-for-conversation-cpi-c-2.md) call to wait for the asynchronous call to complete.<br /><br /> If WaitMode=Block, all verbs are blocking.|  
  
 As with CPICSEND, CPICRECV produces C:\Cpicrecv.out (by default) with timings of the conversations in it.  
  
## Operation  
 CPICRECV should be started first. CPICRECV issues [Specify_Local_TP_Name](../core/specify-local-tp-name-cpi-c-1.md) to set its local TP name, and then [Accept_Conversation](../core/accept-conversation-cpi-c-1.md) to accept a conversation (note that because **Specify_Local_TP_Name** is issued, the **Accept_Conversation** will complete asynchronously).  
  
 Both TPs issue [Specify_Windows_Handle](../core/specify-windows-handle-cpi-c-1.md) during initialization to set either the window handle or NULL. CPICSEND calls [Set_Processing_Mode](../core/set-processing-mode-cpi-c-1.md) after completion of [Initialize_Conversation](../core/initialize-conversation-cpi-c-2.md) to set the processing mode to non-blocking for this conversation.  
  
 After each call is issued, the return code is checked. If the return code is not CM_OPERATION_INCOMPLETE, the call has already completed, so an ASYNC_COMPLETE message is posted to trigger the next call. If **WaitMode** is set to YES and the issued call did not complete immediately, a [Wait_For_Conversation](../core/wait-for-conversation-cpi-c-2.md) call is issued to wait for call completion, at which point an ASYNC_COMPLETE message is posted. If **WaitMode** is set to NO and the issued call did not complete immediately, Windows CPI-C detects call completion and posts an ASYNC_COMPLETE message. The receipt of the ASYNC_COMPLETE message triggers the next call to be issued.  
  
 For CPICSEND, each conversation consists of an [Allocate](../core/allocate-cpi-c-1.md) call, followed by a given number of [Send_Data](../core/send-data-cpi-c-1.md) calls of given size and interspersed with [Confirm](../core/confirm-cpi-c-1.md) calls at a given interval, followed by a [Deallocate](../core/deallocate-cpi-c-2.md).  
  
 CPICRECV issues [Receive](../core/receive-cpi-c-1.md) on completion of the [Accept_Conversation](../core/accept-conversation-cpi-c-1.md), and then issues either **Receive** or [Confirmed](../core/confirmed-cpi-c-1.md) according to the return from the previous **Receive**.  
  
 At any stage, if the TPs encounter an error, they terminate. Use CPI-C API tracing to diagnose problems with the configuration.  
  
 Both TPs are built from a single source-code file, CPICSR.C. CPICSEND is compiled only if CPICSEND macro is #defined. This macro is normally defined using the -DCPICSEND option on the command line to the C compiler.  
  
 The TPs run as Windows Server applications with a minimized window, the title of which displays the status. When the WndProc of this window, TPWndProc, receives the WM_CREATE message for the window, it triggers the issuing of the first call. When TPWndProc receives an ASYNC_COMPLETE message from Windows CPI-C, it triggers the issuing of the next call, dependent on what the previous call was. When the window is closed, [WinCPICCleanup](../core/wincpiccleanup1.md) is issued to terminate any active conversations.  
  
## See Also  
 [CPI-C Samples](../core/cpi-c-samples.md)