---
title: "CONFIRM2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 45f75964-1e09-4cdf-a621-b7d76252234b
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# CONFIRM
The **CONFIRM** verb sends the contents of the local logical unit's (LU) send buffer and a confirmation request to the partner transaction program (TP).  
  
 The following structure describes the verb control block used by the **CONFIRM** verb.  
  
## Syntax  
  
```  
  
struct confirm {  
    unsigned short  opcode;  
    unsigned char   opext;  
    unsigned char   reserv2;  
    unsigned short  primary_rc;  
    unsigned long   secondary_rc;  
    unsigned char   tp_id[8];  
    unsigned long   conv_id;  
    unsigned char   rts_rcvd;  
};   
```  
  
## Remarks  
 **Members**  
  
 *opcode*  
 Supplied parameter. Specifies the verb operation code, AP_B_CONFIRM.  
  
 *opext*  
 Supplied parameter. Specifies the verb operation extension, AP_BASIC_CONVERSATION.  
  
 *reserv2*  
 A reserved field.  
  
 *primary_rc*  
 Returned parameter. Specifies the primary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 *secondary_rc*  
 Returned parameter. Specifies the secondary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 *tp_id*  
 Supplied parameter. Identifies the local TP. The value of this parameter was returned by [TP_STARTED](../core/tp-started2.md).  
  
 *conv_id*  
 Returned parameter. Identifies the conversation established between the two TPs.  
  
 *rts_rcvd*  
 Returned parameter. Indicates whether the partner TP issued [REQUEST_TO_SEND](../core/request-to-send1.md), which requests the local TP to change the conversation to RECEIVE state.  
  
 To change to RECEIVE state operating on Microsoft Windows the local TP can use [PREPARE_TO_RECEIVE](../core/prepare-to-receive2.md), [RECEIVE_AND_WAIT](../core/receive-and-wait2.md), or [RECEIVE_AND_POST](../core/receive-and-post1.md).  
  
 **Return Codes**  
  
 AP_OK  
 Primary return code; the verb executed successfully.  
  
 AP_PARAMETER_CHECK  
 Primary return code; the verb did not execute because of a parameter error.  
  
 AP_BAD_CONV_ID  
  
 Secondary return code; the value of **conv_id** did not match a conversation identifier assigned by APPC.  
  
 AP_BAD_TP_ID  
  
 Secondary return code; the value of **tp_id** did not match a TP identifier assigned by APPC.  
  
 AP_CONFIRM_ON_SYNC_LEVEL_NONE  
  
 Secondary return code; the local TP attempted to use **CONFIRM** in a conversation with a synchronization level of AP_NONE. The synchronization level, established by [ALLOCATE](../core/allocate2.md), must be AP_CONFIRM_SYNC_LEVEL.  
  
 AP_STATE_CHECK  
 Primary return code; the verb did not execute because it was issued in an invalid state.  
  
 AP_CONFIRM_BAD_STATE  
  
 Secondary return code; the conversation was not in SEND state.  
  
 AP_CONFIRM_NOT_LL_BDY  
  
 Secondary return code; the conversation for the local TP was in SEND state, and the local TP did not finish sending a logical record.  
  
 AP_ALLOCATION_ERROR  
 Primary return code; APPC has failed to allocate a conversation. The conversation state is set to RESET.  
  
 This code can be returned through a verb issued after **ALLOCATE**.  
  
 AP_ALLOCATION_FAILURE_NO_RETRY  
  
 Secondary return code; the conversation cannot be allocated because of a permanent condition, such as a configuration error or session protocol error. To determine the error, the system administrator should examine the error log file. Do not retry the allocation until the error has been corrected.  
  
 AP_ALLOCATION_FAILURE_RETRY  
  
 Secondary return code; the conversation could not be allocated because of a temporary condition, such as a link failure. The reason for the failure is logged in the system error log. Retry the allocation.  
  
 AP_CONVERSATION_TYPE_MISMATCH  
  
 Secondary return code; the partner LU or TP does not support the conversation type (basic or mapped) specified in the allocation request.  
  
 AP_PIP_NOT_ALLOWED  
  
 Secondary return code; the allocation request specified PIP data, but either the partner TP does not require this data, or the partner LU does not support it.  
  
 AP_PIP_NOT_SPECIFIED_CORRECTLY  
  
 Secondary return code; the partner TP requires PIP data, but the allocation request specified either no PIP data or an incorrect number of parameters.  
  
 AP_SECURITY_NOT_VALID  
  
 Secondary return code; the user identifier or password specified in the allocation request was not accepted by the partner LU.  
  
 AP_SYNC_LEVEL_NOT_SUPPORTED  
  
 Secondary return code; the partner TP does not support the **sync_level** (AP_NONE, AP_CONFIRM_SYNC_LEVEL, or AP_SYNCPT) specified in the allocation request, or the **sync_level** was not recognized.  
  
 AP_TP_NAME_NOT_RECOGNIZED  
  
 Secondary return code; the partner LU does not recognize the TP name specified in the allocation request.  
  
 AP_TRANS_PGM_NOT_AVAIL_NO_RETRY  
  
 Secondary return code; the remote LU rejected the allocation request because it was unable to start the requested partner TP. The condition is permanent. The reason for the error may be logged on the remote node. Do not retry the allocation until the error has been corrected.  
  
 AP_TRANS_PGM_NOT_AVAIL_RETRY  
  
 Secondary return code; the remote LU rejected the allocation request because it was unable to start the requested partner TP. The condition may be temporary, such as a time-out. The reason for the error may be logged on the remote node. Retry the allocation.  
  
 AP_COMM_SUBSYSTEM_ABENDED  
 Primary return code; indicates one of the following conditions:  
  
- The node used by this conversation encountered an ABEND.  
  
- The connection between the TP and the PU 2.1 node has been broken (a LAN error).  
  
- The SnaBase at the TP's computer has encountered an ABEND.  
  
  The system administrator should examine the error log to determine the reason for the ABEND.  
  
  AP_CONV_FAILURE_NO_RETRY  
  Primary return code; the conversation was terminated because of a permanent condition, such as a session protocol error. The system administrator should examine the system error log to determine the cause of the error. Do not retry the conversation until the error has been corrected.  
  
  AP_CONV_FAILURE_RETRY  
  Primary return code; the conversation was terminated because of a temporary error. Restart the TP to see if the problem occurs again. If it does, the system administrator should examine the error log to determine the cause of the error.  
  
  AP_CONVERSATION_TYPE_MIXED  
  Primary return code; the TP has issued both basic and mapped conversation verbs. Only one type can be issued in a single conversation.  
  
  AP_INVALID_VERB_SEGMENT  
  Primary return code; the VCB extended beyond the end of the data segment.  
  
  AP_PROG_ERROR_PURGING  
  Primary return code; while in RECEIVE, PENDING, PENDING_POST, CONFIRM, CONFIRM_SEND, or CONFIRM_DEALLOCATE state, the partner TP issued [SEND_ERROR](../core/send-error2.md) with **err_type** set to AP_PROG. Data sent but not yet received is purged.  
  
  AP_STACK_TOO_SMALL  
  Primary return code; the stack size of the application is too small to execute the verb. Increase the stack size of your application.  
  
  AP_CONV_BUSY  
  Primary return code; there can only be one outstanding conversation verb at a time on any conversation. This can occur if the local TP has multiple threads, and more than one thread is issuing APPC calls using the same **conv_id**.  
  
  AP_THREAD_BLOCKING  
  Primary return code; the calling thread is already in a blocking call.  
  
  AP_UNEXPECTED_DOS_ERROR  
  Primary return code; the operating system has returned an error to APPC while processing an APPC call from the local TP. The operating system return code is returned through the **secondary_rc**. It appears in Intel byte-swapped order. If the problem persists, consult the system administrator.  
  
  AP_DEALLOC_ABEND_PROG  
  Primary return code; the conversation has been deallocated for one of the following reasons:  
  
- The partner TP issued [DEALLOCATE](../core/deallocate2.md) with **dealloc_type**set to AP_ABEND_PROG.  
  
- The partner TP has encountered an ABEND, causing the partner LU to send a **DEALLOCATE** request.  
  
  AP_DEALLOC_ABEND_SVC  
  Primary return code; the conversation has been deallocated because the partner TP issued **DEALLOCATE** with **dealloc_type** set to AP_ABEND_SVC.  
  
  AP_DEALLOC_ABEND_TIMER  
  Primary return code; the conversation has been deallocated because the partner TP issued **DEALLOCATE** with **dealloc_type** set to AP_ABEND_TIMER.  
  
  AP_SVC_ERROR_PURGING  
  Primary return code; the partner TP (or partner LU) issued [SEND_ERROR](../core/send-error2.md) with **err_type** set to AP_SVC while in RECEIVE, PENDING_POST, CONFIRM, CONFIRM_SEND, or CONFIRM_DEALLOCATE state. Data sent to the partner TP may have been purged.  
  
  **Remarks**  
  
  In response to **CONFIRM**, the partner TP normally issues [CONFIRMED](../core/confirmed1.md) to confirm that it has received the data without error. (If the partner TP encounters an error, it issues [SEND_ERROR](../core/send-error2.md) or abnormally deallocates the conversation.)  
  
  The TP can issue **CONFIRM** only if the conversation's synchronization level, established by [ALLOCATE](../core/allocate2.md), is AP_CONFIRM_SYNC_LEVEL.  
  
  The conversation must be in SEND state when the TP issues this verb. State changes, summarized in the following table, are based on the value of the **primary_rc**.  
  
|primary_rc|New state|  
|-----------------|---------------|  
|AP_OK|No change|  
|AP_ALLOCATION_ERROR|RESET|  
|AP_COMM_SUBSYSTEM_ABENDED AP_COMM_SUBSYSTEM_NOT_LOADED|RESET RESET|  
|AP_CONV_FAILURE_RETRY AP_CONV_FAILURE_NO_RETRY|RESET RESET|  
|AP_DEALLOC_ABEND AP_DEALLOC_ABEND_PROG AP_DEALLOC_ABEND_SVC AP_DEALLOC_ABEND_TIMER|RESET RESET RESET RESET|  
|AP_PROG_ERROR_PURGING AP_SVC_ERROR_PURGING|RECEIVE RECEIVE|  
  
 **CONFIRM** waits for a response from the partner TP. A response is generated by one of the following verbs in the partner TP:  
  
- [CONFIRMED](../core/confirmed1.md)  
  
- [SEND_ERROR](../core/send-error2.md)  
  
- [DEALLOCATE](../core/deallocate2.md) with **dealloc_type** set to AP_ABEND_PROG, AP_ABEND_SVC, or AP_ABEND_TIMER  
  
- [TP_ENDED](../core/tp-ended1.md)  
  
  By issuing **CONFIRM** after[ALLOCATE](../core/allocate2.md), the invoking TP can immediately determine whether the allocation was successful (if **synclevel** is set to AP_CONFIRM_SYNC_LEVEL).  
  
  Normally, the value of the **ALLOCATE** verb's **mode_name** parameter must match the name of a mode configured for the invoked TP's node and associated during configuration with the partner LU.  
  
  If one of the modes associated with the partner LU on the invoked TP's node is an implicit mode, the session established between the two LUs will be of the implicit mode when no mode name associated with the partner LU matches the value of **mode_name**. For more information, see Host Integration Server Help.  
  
  Several parameters of **ALLOCATE** are EBCDIC or ASCII strings. A TP can use the common service verb (CSV) [CONVERT](../core/convert2.md) to translate a string from one character set to the other.  
  
  To send the **ALLOCATE** request immediately, the invoking TP can issue [FLUSH](../core/flush2.md) or **CONFIRM** immediately after **ALLOCATE**. Otherwise, the **ALLOCATE** request accumulates with other data in the local LU's send buffer until the buffer is full.