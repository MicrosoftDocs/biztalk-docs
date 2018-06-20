---
title: "PREPARE_TO_RECEIVE2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1b7f05d7-cddd-40c5-a1fc-51b8b607400d
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# PREPARE_TO_RECEIVE
The **PREPARE_TO_RECEIVE** verb changes the state of the conversation for the local transaction program (TP) from SEND to RECEIVE.  
  
 The following structure describes the verb control block (VCB) used by the **PREPARE_TO_RECEIVE** verb.  
  
## Syntax  
  
```  
  
struct prepare_to_receive {  
    unsigned short   opcode;  
    unsigned char    opext;  
    unsigned char    primary_rc;  
    unsigned short   reserv2;  
    unsigned long    secondary_rc;  
    unsigned char    tp_id[8];  
    unsigned long    conv_id;  
    unsigned char    ptr_type;  
    unsigned char    locks;  
};   
```  
  
## Members  
 *opcode*  
 Supplied parameter. Specifies the verb operation code, AP_B_PREPARE_TO_RECEIVE.  
  
 *opext*  
 Supplied parameter. Specifies the verb operation extension, AP_BASIC_CONVERSATION.  
  
 *reserv2*  
 A reserved field.  
  
 *primary_rc*  
 Returned parameter. Specifies the primary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 *secondary_rc*  
 Returned parameter. Specifies the secondary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 *tp_id*  
 Supplied parameter. Identifies the local TP. The value of this parameter is returned by [TP_STARTED](../core/tp-started2.md) in the invoking TP or by[RECEIVE_ALLOCATE](../core/receive-allocate1.md) in the invoked TP.  
  
 *conv_id*  
 Supplied parameter. Provides the conversation identifier. The value of this parameter is returned by [ALLOCATE](../core/allocate2.md)in the invoking TP or by **RECEIVE_ALLOCATE** in the invoked TP.  
  
 *ptr_type*  
 Supplied parameter. Specifies how to perform the state change.  
  
 Use AP_FLUSH to send the contents of the local logical unit's (LU) send buffer to the partner LU (and TP) before changing the conversation's state to RECEIVE.  
  
 The AP_SYNC_LEVEL value uses the conversation's synchronization level (established by **ALLOCATE**) to determine how to perform the state change.  
  
 If the synchronization level of the conversation is AP_NONE, APPC sends the contents of the local LU's send buffer to the partner TP before changing the conversation's state to RECEIVE. If the synchronization level is AP_CONFIRM_SYNC_LEVEL, APPC sends the contents of the local LU's send buffer and a confirmation request to the partner TP. Upon receiving confirmation from the partner TP, APPC changes the conversation's state to RECEIVE. If, however, the partner TP reports an error, the state changes to RECEIVE or RESET. See the Remarks in this topic.  
  
 *locks*  
 Supplied parameter. Specifies when APPC should return control to the local TP.  
  
 Use this parameter only if **ptr_type** is set to AP_SYNC_LEVEL and the synchronization level of the conversation, established by [ALLOCATE](../core/allocate2.md), is AP_CONFIRM_SYNC_LEVEL. (Otherwise, the parameter is ignored.)  
  
 Use AP_LONG to indicate that APPC returns control to the local TP when the confirmation and subsequent data from the partner TP arrive at the local LU. (This method results in more efficient use of the network but requires a longer time to return control to the local TP.)  
  
 Use AP_SHORT to indicate that APPC returns control to the local TP when the confirmation from the partner TP arrives at the local LU.  
  
## Return Codes  
 AP_OK  
 Primary return code; the verb executed successfully.  
  
 AP_PARAMETER_CHECK  
 Primary return code; the verb did not execute because of a parameter error.  
  
 AP_BAD_CONV_ID  
  
 Secondary return code; the value of **conv_id** did not match a conversation identifier assigned by APPC.  
  
 AP_BAD_TP_ID  
  
 Secondary return code; the value of **tp_id** did not match a TP identifier assigned by APPC.  
  
 AP_P_TO_R_INVALID_TYPE  
  
 Secondary return code; the **ptr_type** parameter was not set to a valid value.  
  
 AP_STATE_CHECK  
 Primary return code; the verb did not execute because it was issued in an invalid state.  
  
 AP_P_TO_R_NOT_SEND_STATE  
  
 Secondary return code; the conversation was not in SEND state.  
  
 AP_P_TO_R_NOT_LL_BDY  
  
 Secondary return code; the local TP did not finish sending a logical record.  
  
 AP_ALLOCATION_ERROR  
 Primary return code; APPC has failed to allocate a conversation. The conversation state is set to RESET.  
  
 This code can be returned through a verb issued after [ALLOCATE](../core/allocate2.md).  
  
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
  
 Secondary return code; the partner TP does not support the **sync_level** (AP_NONE or AP_CONFIRM_SYNC_LEVEL) specified in the allocation request, or the **sync_level** was not recognized.  
  
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
  
- The SnaBase at the TP's computer encountered an ABEND.  
  
  The system administrator should examine the error log to determine the reason for the ABEND.  
  
  AP_COMM_SUBSYSTEM_NOT_LOADED  
  Primary return code; a required component could not be loaded or terminated while processing the verb. Thus, communication could not take place. Contact the system administrator for corrective action.  
  
  When this return code is used with [ALLOCATE](../core/allocate2.md), it can indicate that no communications system could be found to support the local LU. (For example, the local LU alias specified with [TP_STARTED](../core/tp-started2.md) is incorrect or has not been configured.) Note that if **lu_alias** or **mode_name** is fewer than eight characters, you must ensure that these fields are filled with spaces to the right. This error is returned if these parameters are not filled with spaces, since there is no node available that can satisfy the **ALLOCATE** request.  
  
  When **ALLOCATE** produces this return code for a Host Integration Server Client system configured with multiple nodes, there are two secondary return codes as follows:  
  
  0xF0000001  
  
  Secondary return code; no nodes have been started.  
  
  0xF0000002  
  
  Secondary return code; at least one node has been started, but the local LU (when **TP_STARTED** is issued) is not configured on any active nodes. The problem could be either of the following:  
  
- The node with the local LU is not started.  
  
- The local LU is not configured.  
  
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
  
- The partner TP issued [DEALLOCATE](../core/deallocate2.md) with **dealloc_type** set to AP_ABEND_PROG.  
  
- The partner TP has encountered an ABEND, causing the partner LU to send a **DEALLOCATE** request.  
  
  AP_DEALLOC_ABEND_SVC  
  Primary return code; the conversation has been deallocated because the partner TP issued **DEALLOCATE** with **dealloc_type** set to AP_ABEND_SVC.  
  
  AP_DEALLOC_ABEND_TIMER  
  Primary return code; the conversation has been deallocated because the partner TP issued **DEALLOCATE** with **dealloc_type** set to AP_ABEND_TIMER.  
  
  AP_SVC_ERROR_PURGING  
  Primary return code; the partner TP (or partner LU) issued a [SEND_ERROR](../core/send-error2.md) verb with **err_type** set to AP_SVC while in RECEIVE, PENDING_POST, CONFIRM, CONFIRM_SEND, or CONFIRM_DEALLOCATE state. Data sent to the partner TP may have been purged.  
  
## Remarks  
 Before changing the conversation state, this verb performs the equivalent of one of the following:  
  
- [FLUSH](../core/flush2.md), by sending the contents of the local LU's send buffer to the partner LU (and TP).  
  
- [CONFIRM](../core/confirm2.md), by sending the contents of the local LU's send buffer and a confirmation request to the partner TP.  
  
  After this verb has successfully executed, the local TP can receive data.  
  
  The conversation must be in SEND state when the TP issues this verb.  
  
  State changes, summarized in the following table, are based on the value of **primary_rc**.  
  
|primary_rc|New state|  
|-----------------|---------------|  
|AP_OK|RECEIVE|  
|AP_ALLOCATION_ERROR|RESET|  
|AP_CONV_FAILURE_RETRY|RESET|  
|AP_CONV_FAILURE_NO_RETRY|RESET|  
|AP_DEALLOC_ABEND|RESET|  
|AP_DEALLOC_ABEND_PROG|RESET|  
|AP_DEALLOC_ABEND_SVC|RESET|  
|AP_DEALLOC_ABEND_TIMER|RESET|  
|AP_PROG_ERROR_PURGING|RECEIVE|  
|AP_SVC_ERROR_PURGING|RECEIVE|  
  
 The conversation does not change to SEND state for the partner TP until the partner TP receives one of the following values through the **what_rcvd** parameter of a subsequent receive verb:  
  
- AP_SEND  
  
- AP_CONFIRM_SEND and replies with [CONFIRMED](../core/confirmed1.md)  
  
- AP_DATA_COMPLETE_CONFIRM_SEND and replies with **CONFIRMED**  
  
- AP_DATA_CONFIRM_SEND and replies with **CONFIRMED**  
  
  The receive verbs are [RECEIVE_AND_POST](../core/receive-and-post1.md), [RECEIVE_IMMEDIATE](../core/receive-immediate1.md), and [RECEIVE_AND_WAIT](../core/receive-and-wait2.md).