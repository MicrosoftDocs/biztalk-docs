---
title: "Primary APPC Return Codes1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 794de4ff-0b92-4351-84ac-62ea12efddc6
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Primary APPC Return Codes
## 0000  
 AP_OK  
 The verb executed successfully.  
  
## 0001  
 AP_PARAMETER_CHECK  
 The verb did not execute because of a parameter error.  
  
## 0002  
 AP_STATE_CHECK  
 The verb did not execute because it was issued in an invalid state.  
  
## 0003  
 AP_ALLOCATION_ERROR  
 APPC failed to allocate a conversation. The conversation state is set to RESET.  
  
 This code can be returned through a verb issued after [ALLOCATE](../core/allocate2.md) or [MC_ALLOCATE](../core/mc-allocate2.md).  
  
## 0005  
 AP_DEALLOC_ABEND (for a mapped conversation)  
 The conversation has been deallocated for one of the following reasons:  
  
-   The partner transaction program (TP) issued [MC_DEALLOCATE](../core/mc-deallocate2.md) with **dealloc_type** set to AP_ABEND.  
  
-   The partner TP encountered an ABEND, causing the partner logical unit (LU) to send an **MC_DEALLOCATE** request.  
  
## 0006  
 AP_DEALLOC_ABEND_PROG (for a basic conversation)  
 The conversation has been deallocated for one of the following reasons:  
  
-   The partner TP issued [DEALLOCATE](../core/deallocate2.md) with **dealloc_type** set to AP_ABEND_PROG.  
  
-   The partner TP encountered an ABEND, causing the partner LU to send a **DEALLOCATE** request.  
  
## 0007  
 AP_DEALLOC_ABEND_SVC (for a basic conversation)  
 The conversation has been deallocated because the partner TP issued [DEALLOCATE](../core/deallocate2.md) with **dealloc_type** set to AP_ABEND_SVC.  
  
## 0008  
 AP_DEALLOC_ABEND_TIMER (for a basic conversation)  
 The conversation has been deallocated because the partner TP issued [DEALLOCATE](../core/deallocate2.md) with **dealloc_type** set to AP_ABEND_TIMER.  
  
## 0009  
 AP_DEALLOC_NORMAL  
 The partner TP has deallocated the conversation without requesting confirmation.  
  
## 000C  
 AP_PROG_ERROR_NO_TRUNC  
 The partner TP has issued one of the following verbs while the conversation was in SEND state:  
  
- [SEND_ERROR](../core/send-error2.md) with **err_type** set to AP_PROG  
  
- [MC_SEND_ERROR](../core/mc-send-error2.md)  
  
  Data was not truncated.  
  
## 000F  
 AP_CONV_FAILURE_RETRY  
 The conversation was terminated because of a temporary error. Restart the TP to see if the problem occurs again. If it does, the system administrator should examine the error log to determine the cause of the error.  
  
## 0010  
 AP_CONV_FAILURE_NO_RETRY  
 The conversation was terminated because of a permanent condition, such as a session protocol error. The system administrator should examine the system error log to determine the cause of the error. Do not retry the conversation until the error has been corrected.  
  
## 0011  
 AP_SVC_ERROR_NO_TRUNC  
 While in SEND state, the partner TP (or partner LU) issued [SEND_ERROR](../core/send-error2.md) with **err_type** set to AP_SVC. Data was not truncated.  
  
## 0012  
 AP_PROG_ERROR_TRUNC/AP_SVC_ERROR_TRUNC  
 In SEND state, after sending an incomplete logical record, the partner TP issued [SEND_ERROR](../core/send-error2.md). The local TP may have received the first part of the logical record.  
  
## 0013  
 AP_SVC_ERROR_PURGING  
 The partner TP (or partner LU) issued [SEND_ERROR](../core/send-error2.md) with **err_type** set to AP_SVC while in RECEIVE, PENDING_POST, CONFIRM, CONFIRM_SEND, or CONFIRM_DEALLOCATE state. Data sent to the partner TP may have been purged.  
  
## 0014  
 AP_UNSUCCESSFUL  
 No data is immediately available from the partner TP.  
  
## 0017  
 AP_CNOS_LOCAL_RACE_REJECT  
 APPC is currently processing a [CNOS](../core/cnos2.md) verb issued by a local LU.  
  
## 0018  
 AP_CNOS_PARTNER_LU_REJECT  
 The partner LU rejected a [CNOS](../core/cnos2.md) request from the local LU.  
  
## 0019  
 AP_CONVERSATION_TYPE_MIXED  
 The TP has issued both basic and mapped conversation verbs. Only one type can be issued in a single conversation.  
  
## 0021  
 AP_CANCELED  
 The local TP issued one of the following verbs, which canceled [RECEIVE_AND_POST](../core/receive-and-post1.md) or [MC_RECEIVE_AND_POST](../core/mc-receive-and-post2.md):  
  
- [DEALLOCATE](../core/deallocate2.md) with **dealloc_type** set to AP_ABEND_PROG, AP_ABEND_SVC, or AP_ABEND_TIMER  
  
- [MC_DEALLOCATE](../core/mc-deallocate2.md) with **dealloc_type** set to AP_ABEND  
  
- [SEND_ERROR](../core/send-error2.md) or [MC_SEND_ERROR](../core/mc-send-error2.md)  
  
- [TP_ENDED](../core/tp-ended1.md)  
  
  Issuing one of these verbs causes the semaphore to be cleared.  
  
## F002  
 AP_TP_BUSY  
 The local TP has issued a call to APPC while APPC was processing another call for the same TP. This can occur if the local TP has multiple threads, and more than one thread is issuing APPC calls using the same **tp_id**.  
  
## F003  
 AP_COMM_SUBSYSTEM_ABENDED  
 Indicates one of the following conditions:  
  
- The node used by this conversation encountered an ABEND.  
  
- The connection between the TP and the PU 2.1 node has been broken (a LAN error).  
  
- The SnaBase at the TP's computer encountered an ABEND.  
  
  The system administrator should examine the error log to determine the reason for the ABEND.  
  
## F004  
 AP_COMM_SUBSYSTEM_NOT_LOADED  
 A required component could not be loaded or has terminated while processing the verb. Thus, communication could not take place. Contact the system administrator for corrective action.  
  
## F005  
 AP_CONV_BUSY  
 There can only be one outstanding conversation verb at a time on any conversation.  
  
## F006  
 AP_THREAD_BLOCKING  
 The calling thread is already in a blocking call.  
  
## F008  
 AP_INVALID_VERB_SEGMENT  
 The verb control block (VCB) extended beyond the end of the data segment.  
  
## F011  
 AP_UNEXPECTED_DOS_ERROR  
 The operating system returned an error to APPC while processing an APPC call from the local TP. The operating system return code is returned through the **secondary_rc**. It appears in Intel byte-swapped order. If the problem persists, consult the system administrator.  
  
## F015  
 AP_STACK_TOO_SMALL  
 The stack size of the application is too small to execute the verb. Increase the stack size of your application.  
  
## F020  
 AP_INVALID_KEY  
 The supplied **key** was incorrect.