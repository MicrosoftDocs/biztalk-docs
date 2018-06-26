---
title: "MC_POST_ON_RECEIPT1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dc9f6d9f-4c02-4a1d-8e82-b2a5da7e8eef
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# MC_POST_ON_RECEIPT
The **MC_POST_ON_RECEIPT** verb allows the application to register to receive a notification when data or status arrives at the local logical unit (LU) without actually receiving it at the same time. This verb can only be issued while in RECEIVE state and it never causes a change in conversation state.  
  
 When the transaction program (TP) issues this verb, APPC returns control to the TP immediately. When the specified conditions are satisfied, the Win32® event specified by the **sema** parameter is signaled and the verb completes. Then the TP looks at the return code in the verb control block (VCB) to determine whether or not any data or status notification has arrived at the local LU and issues an [MC_RECEIVE_IMMEDIATE](../core/mc-receive-immediate2.md) or [MC_RECEIVE_AND_WAIT](../core/mc-receive-and-wait2.md) verb to actually receive the data or status notification.  
  
 The **MC_POST_ON_RECEIPT** verb implements both the **POST_ON_RECEIPT** and **TEST** verbs as described in the IBM Transaction Programmer's manual for LU Type 6.2.  
  
 The following structure describes the verb control block used by the **MC_POST_ON_RECEIPT** verb.  
  
## Syntax  
  
```  
  
struct mc_post_on_receipt {  
    unsigned short   opcode;  
    unsigned char    opext;  
    unsigned char    reserv1;  
    unsigned char    primary_rc;  
    unsigned long    secondary_rc;  
    unsigned char    tp_id[8];  
    unsigned long    conv_id;  
    unsigned short   reserv2;  
    unsigned char    reserv3;  
    unsigned char    reserv4;  
    unsigned short   max_len;  
    unsigned short   reserv5;  
    unsigned char *  reserv6;  
    unsigned char    reserv7[5];  
    unsigned long    sema;  
};   
```  
  
## Members  
 *opcode*  
 Supplied parameter. Specifies the verb operation code, AP_M_POST_ON_RECEIPT.  
  
 *opext*  
 Supplied parameter. Specifies the verb operation extension, AP_MAPPED_CONVERSATION.  
  
 *reserv1*  
 A reserved field.  
  
 *primary_rc*  
 Returned parameter. Specifies the primary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 *secondary_rc*  
 Returned parameter. Specifies the secondary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 *tp_id*  
 Supplied parameter. Identifies the local TP. The value of this parameter is returned by [TP_STARTED](../core/tp-started2.md) in the invoking TP or by[RECEIVE_ALLOCATE](../core/receive-allocate1.md) in the invoked TP.  
  
 *conv_id*  
 Supplied parameter. Provides the conversation identifier. The value of this parameter is returned by [MC_ALLOCATE](../core/mc-allocate2.md) in the invoking TP or by **RECEIVE_ALLOCATE** in the invoked TP.  
  
 *reserv2*  
 A reserved field.  
  
 *reserv3*  
 A reserved field.  
  
 *reserv4*  
 A reserved field.  
  
 *max_len*  
 Supplied parameter. Specifies the length of data that triggers APPC to post a notification to the TP.  
  
 *reserv5*  
 A reserved field.  
  
 *reserv6*  
 A reserved field.  
  
 *reserv7*  
 A reserved field.  
  
 *sema*  
 Supplied parameter. Specifies the handle of a Win32 event. The event should have been created by the TP and the TP is responsible for ensuring that it is reset before a call is made and after the verb completes.  
  
## Return Codes  
 AP_OK  
 Primary return code; the verb executed successfully.  
  
 AP_DATA  
  
 Secondary return code; data is available for the program to receive.  
  
 AP_NOT_DATA  
  
 Secondary return code; information other than data is available for the program to receive.  
  
 AP_CANCELLED  
 Primary return code; the verb was canceled.  
  
 AP_PARAMETER_CHECK  
 Primary return code; the verb did not execute because of a parameter error.  
  
 AP_BAD_CONV_ID  
  
 Secondary return code; the value of **conv_id** did not match a conversation identifier assigned by APPC.  
  
 AP_BAD_TP_ID  
  
 Secondary return code; the value of **tp_id** did not match a TP identifier assigned by APPC.  
  
 AP_INVALID_SEMAPHORE_HANDLE  
  
 Secondary return code; the **sema** parameter was not set to a valid value.  
  
 AP_STATE_CHECK  
 Primary return code; the verb did not execute because it was issued in an invalid state.  
  
 AP_ALLOCATION_ERROR  
 Primary return code; APPC has failed to allocate a conversation. The conversation state is set to RESET.  
  
 This code can be returned through a verb issued after [MC_ALLOCATE](../core/mc-allocate2.md).  
  
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
  
  AP_DEALLOC_ABEND_PROG  
  Primary return code; the conversation has been deallocated for one of the following reasons:  
  
- The partner TP issued [MC_DEALLOCATE](../core/mc-deallocate2.md).  
  
- The partner TP has encountered an ABEND, causing the partner LU to send an **MC_DEALLOCATE** request.  
  
  AP_DEALLOC_NORMAL  
  Primary return code; the partner TP has deallocated the conversation without requesting confirmation and issued [MC_DEALLOCATE](../core/mc-deallocate2.md) with **dealloc_type** set to one of the following:  
  
- AP_CONFIRM_SYNC_LEVEL  
  
- AP_FLUSH  
  
- AP_SYNC_LEVEL with the synchronization level of the conversation specified as AP_NONE  
  
  AP_PROG_ERROR_NO_TRUNC  
  Primary return code; the partner TP has issued [MC_SEND_ERROR](../core/mc-send-error2.md) while the conversation was in SEND state. Data was not truncated.  
  
  AP_PROG_ERROR_PURGING  
  Primary return code; while in RECEIVE, PENDING, PENDING_POST, CONFIRM, CONFIRM_SEND, or CONFIRM_DEALLOCATE state, the partner TP issued [MC_SEND_ERROR](../core/mc-send-error2.md). Data sent but not yet received is purged.  
  
  AP_PROG_ERROR_TRUNC  
  Primary return code; the partner TP has issued [MC_SEND_ERROR](../core/mc-send-error2.md) while the conversation was in SEND state. Data was truncated.  
  
  AP_SVC_ERROR_NO_TRUNC  
  Primary return code; the partner TP (or partner LU) issued [MC_SEND_ERROR](../core/mc-send-error2.md) with **err_type** set to AP_SVC while in RECEIVE, PENDING_POST, CONFIRM, CONFIRM_SEND, or CONFIRM_DEALLOCATE state. Data sent to the partner TP was not truncated.  
  
  AP_SVC_ERROR_PURGING  
  Primary return code; the partner TP (or partner LU) issued [MC_SEND_ERROR](../core/mc-send-error2.md) with **err_type** set to AP_SVC while in RECEIVE, PENDING_POST, CONFIRM, CONFIRM_SEND, or CONFIRM_DEALLOCATE state. Data sent to the partner TP may have been purged.  
  
  AP_SVC_ERROR_TRUNC  
  Primary return code; the partner TP (or partner LU) issued [MC_SEND_ERROR](../core/mc-send-error2.md) with **err_type** set to AP_SVC while in RECEIVE, PENDING_POST, CONFIRM, CONFIRM_SEND, or CONFIRM_DEALLOCATE state. Data sent to the partner TP may have been truncated.  
  
## Remarks  
 While an **MC_POST_ON_RECEIPT** verb is outstanding, the following verbs can be issued on the same conversation:  
  
 [GET_ATTRIBUTES](../core/get-attributes2.md)  
  
 [GET_TYPE](../core/get-type2.md)  
  
 [MC_DEALLOCATE](../core/mc-deallocate2.md)  
  
 [MC_RECEIVE_AND_WAIT](../core/mc-receive-and-wait2.md)  
  
 [MC_RECEIVE_IMMEDIATE](../core/mc-receive-immediate2.md)  
  
 [MC_REQUEST_TO_SEND](../core/mc-request-to-send1.md)  
  
 [MC_SEND_ERROR](../core/mc-send-error2.md)  
  
 [MC_TEST_RTS](../core/mc-test-rts2.md)  
  
 [TP_ENDED](../core/tp-ended1.md)  
  
 Issuing any of the following verbs prior to completion of the asynchronous **MC_POST_ON_RECEIPT** verb causes the **MC_POST_ON_RECEIPT** verb to be canceled (the Win32 event is signaled and the primary return code in the verb control block is set to AP_CANCELLED).  
  
 [MC_DEALLOCATE](../core/mc-deallocate2.md)  
  
 [MC_RECEIVE_AND_WAIT](../core/mc-receive-and-wait2.md)  
  
 [MC_RECEIVE_IMMEDIATE](../core/mc-receive-immediate2.md)  
  
 [MC_SEND_ERROR](../core/mc-send-error2.md)  
  
 [TP_ENDED](../core/tp-ended1.md)