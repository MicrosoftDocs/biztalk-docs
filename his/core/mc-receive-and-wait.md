---
title: "MC_RECEIVE_AND_WAIT2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4a64f995-ff06-4382-ae0c-c502feec7843
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# MC_RECEIVE_AND_WAIT
The **MC_RECEIVE_AND_WAIT** verb receives any data that is currently available from the partner transaction program (TP). If no data is currently available, the local TP waits for data to arrive.  
  
 To allow full use to be made of the asynchronous support, asynchronously issued **MC_RECEIVE_AND_WAIT** verbs have been altered to act like [MC_RECEIVE_AND_POST](../core/mc-receive-and-post.md) verbs. Specifically, while an asynchronous **MC_RECEIVE_AND_WAIT** is outstanding, the following verbs can be issued on the same conversation:  
  
-   [GET_TYPE](../core/get-type.md)  
  
-   [MC_GET_ATTRIBUTES](../core/mc-get-attributes.md)  
  
-   [MC_REQUEST_TO_SEND](../core/mc-request-to-send.md)  
  
-   [MC_SEND_ERROR](../core/mc-send-error.md)  
  
-   [MC_TEST_RTS](../core/mc-test-rts.md)  
  
-   [TP_ENDED](../core/tp-ended.md)  
  
 This allows an application, and in particular, a 5250 emulator, to use an asynchronous **MC_RECEIVE_AND_WAIT** to receive data. While the **MC_RECEIVE_AND_WAIT** is outstanding, it can still use **MC_SEND_ERROR** and **MC_REQUEST_TO_SEND**. It is recommended that you use this feature for full asynchronous support.  
  
 The following structure describes the verb control block (VCB) used by the **MC_RECEIVE_AND_WAIT** verb.  
  
## Syntax  
  
```  
  
struct mc_receive_and_wait {  
    unsigned short      opcode;  
    unsigned char       opext;  
    unsigned char       reserv2;  
    unsigned short      primary_rc;  
    unsigned long       secondary_rc;  
    unsigned char       tp_id[8];  
    unsigned long       conv_id;  
    unsigned short      what_rcvd;  
    unsigned char       rtn_status;  
    unsigned char       reserv4;  
    unsigned char       rts_rcvd;  
    unsigned char       reserv5;  
    unsigned short      max_len;  
    unsigned short      dlen;  
    unsigned char FAR * dptr;  
    unsigned char       reserv6[5];  
};   
```  
  
## Members  
 *opcode*  
 Supplied parameter. Specifies the verb operation code, AP_M_RECEIVE_AND_WAIT.  
  
 *opext*  
 Supplied parameter. Specifies the verb operation extension, AP_MAPPED_CONVERSATION.  
  
 *reserv2*  
 A reserved field.  
  
 *primary_rc*  
 Returned parameter. Specifies the primary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 *secondary_rc*  
 Returned parameter. Specifies the secondary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 *tp_id*  
 Supplied parameter. Identifies the local TP.  
  
 The value of this parameter is returned by [TP_STARTED](../core/tp-started.md) in the invoking TP or by [RECEIVE_ALLOCATE](../core/receive-allocate.md) in the invoked TP.  
  
 *conv_id*  
 Supplied parameter. Specifies the conversation identifier.  
  
 The value of this parameter is returned by [MC_ALLOCATE](../core/mc-allocate.md) in the invoking TP or by **RECEIVE_ALLOCATE** in the invoked TP.  
  
 *what_rcvd*  
 Returned parameter. Indicates whether data or conversation status was received.  
  
-   AP_CONFIRM_DEALLOCATE indicates that the partner TP has issued [MC_DEALLOCATE](../core/mc-deallocate.md) with **dealloc_type** set to AP_SYNC_LEVEL, and the conversation's synchronization level, established by **MC_ALLOCATE**, is AP_CONFIRM_SYNC_LEVEL. Upon receiving this value, the local TP normally issues [MC_CONFIRMED](../core/mc-confirmed.md).  
  
-   AP_CONFIRM_SEND indicates that the partner TP has issued [MC_PREPARE_TO_RECEIVE](../core/mc-prepare-to-receive.md) with **ptr_type** set to AP_SYNC_LEVEL, and the conversation's synchronization level, established by **MC_ALLOCATE**, is AP_CONFIRM_SYNC_LEVEL. Upon receiving this value, the local TP normally issues **MC_CONFIRMED** and begins to send data.  
  
-   AP_CONFIRM_WHAT_RECEIVED indicates that the partner TP has issued [MC_CONFIRM](../core/mc-confirm.md). Upon receiving this value, the local TP normally issues **MC_CONFIRMED**.  
  
-   AP_DATA_COMPLETE indicates, for **MC_RECEIVE_AND_WAIT**, that the local TP has received a complete data record or the last part of a data record. Upon receiving this value, the local TP normally reissues **MC_RECEIVE_AND_WAIT** or issues another receive verb. If the partner TP has sent more data, the local TP begins to receive a new unit of data.  
  
     Otherwise, the local TP examines status information, if **primary_rc** contains AP_OK and **what_rcvd** contains AP_SEND, AP_CONFIRM_SEND, AP_CONFIRM_DEALLOCATE, or AP_CONFIRM_WHAT_RECEIVED.  
  
     See Return Codes in this topic for the next action the local TP normally takes.  
  
     If primary_rc contains AP_DEALLOC_NORMAL, the conversation has been deallocated in response to [MC_DEALLOCATE](../core/mc-deallocate.md) issued by the partner TP.  
  
-   AP_DATA_INCOMPLETE indicates that the local TP has received an incomplete data record. The **max_len** parameter specified a value less than the length of the data record (or less than the remainder of the data record if this is not the first receive verb to read the record). Upon receiving this value, the local TP normally reissues **MC_RECEIVE_AND_WAIT** (or issues another receive verb) to receive the next part of the record.  
  
-   AP_NONE indicates that the TP did not receive data or conversation status indicators.  
  
-   AP_SEND indicates, for the partner TP, that the conversation has entered RECEIVE state. For the local TP, the conversation is now in SEND state. Upon receiving this value, the local TP normally uses [MC_SEND_DATA](../core/mc-send-data.md) to begin sending data.  
  
 *rtn_status*  
 Supplied parameter. Indicates whether both data and conversation status indicators should be returned within one API call.  
  
-   AP_NO specifies that indicators should be returned individually on separate invocations of the verb.  
  
-   AP_YES specifies that indicators should be returned together, provided both are available. Both can be returned when:  
  
     The receive buffer is large enough to hold all of the data that precedes the status indicator.  
  
     The data is the last data record before the status indicator.  
  
 *rts_rcvd*  
 Returned parameter. Contains the request-to-send indicator.  
  
-   AP_YES indicates that the partner TP has issued [MC_REQUEST_TO_SEND](../core/mc-request-to-send.md), which requests that the local TP change the conversation to RECEIVE state.  
  
-   AP_NO indicates that the partner TP has not issued **MC_REQUEST_TO_SEND**.  
  
 *max_len*  
 Supplied parameter. Indicates the maximum number of bytes of data the local TP can receive. The range is from 0 through 65535.  
  
 For the Microsoft Windows operating system and the Windows graphical environment, this value must not exceed the length of the buffer to contain the received data.  
  
 For the OS/2 operating system, the offset of **dptr** plus the value of **max_len** must not exceed the size of the data segment.  
  
 By issuing **MC_RECEIVE_AND_WAIT** with **max_len** set to zero, the local TP can determine whether the partner TP has data to send, seeks confirmation, or has changed the conversation state.  
  
 *dlen*  
 Returned parameter. Indicates the number of bytes of data received. Data is stored in the buffer specified by **dptr**. A length of zero indicates that no data was received.  
  
 *dptr*  
 Supplied parameter. Provides the address of the buffer to contain the data received by the local TP.  
  
 For the Windows operating system and the Windows graphical environment, the data buffer can reside in a static data area or in a globally allocated area. The data buffer must fit entirely within this area.  
  
 For the OS/2 operating system, the data buffer must reside on an unnamed, shared segment, which is allocated by the **DosAllocSeg** function with Flags equal to 1. The data buffer must fit entirely on the data segment.  
  
 For the Windows environment, the data buffer can reside in a static data area or in a globally allocated area. The data buffer must fit entirely within this area.  
  
## Return Codes  
 AP_OK  
 Primary return code; the verb executed successfully.  
  
 When **rtn_status** is AP_YES, the preceding return code or one of the following return codes can be returned.  
  
 AP_DATA_COMPLETE_SEND  
  
 Primary return code; this is a combination of AP_DATA_COMPLETE and AP_SEND.  
  
 AP_DATA_COMPLETE_CONFIRM_SEND  
  
 Primary return code; this is a combination of AP_DATA_COMPLETE and AP_CONFIRM_SEND.  
  
 AP_DATA_COMPLETE_CONFIRM  
  
 Primary return code; this is a combination of AP_DATA_COMPLETE and AP_CONFIRM_WHAT_RECEIVED.  
  
 AP_DATA_COMPLETE_CONFIRM_DEALL  
  
 Primary return code; this is a combination of AP_DATA_COMPLETE and AP_CONFIRM_DEALLOCATE.  
  
 AP_DEALLOC_NORMAL  
 Primary return code; the partner TP has deallocated the conversation without requesting confirmation and issued [MC_DEALLOCATE](../core/mc-deallocate.md) with **dealloc_type** set to one of the following:  
  
-   AP_CONFIRM_SYNC_LEVEL  
  
-   AP_FLUSH  
  
-   AP_SYNC_LEVEL with the synchronization level of the conversation specified as AP_NONE  
  
 If **rtn_status** is AP_YES, examine **what_rcvd** also.  
  
 AP_PARAMETER_CHECK  
 Primary return code; the verb did not execute because of a parameter error.  
  
 AP_BAD_CONV_ID  
  
 Secondary return code; the value of **conv_id** did not match a conversation identifier assigned by APPC.  
  
 AP_BAD_TP_ID  
  
 Secondary return code; the value of **tp_id** did not match a TP identifier assigned by APPC.  
  
 AP_BAD_RETURN_STATUS_WITH_DATA  
  
 Secondary return code; the specified **rtn_status** value was not recognized by APPC.  
  
 AP_INVALID_DATA_SEGMENT  
  
 Secondary return code; the length specified for the data buffer was longer than the segment allocated to contain the buffer.  
  
 AP_STATE_CHECK  
 Primary return code; the verb did not execute because it was issued in an invalid state.  
  
 AP_RCV_AND_WAIT_BAD_STATE  
  
 Secondary return code; the conversation was not in RECEIVE or SEND state when the TP issued this verb.  
  
 AP_ALLOCATION_ERROR  
 Primary return code; APPC has failed to allocate a conversation. The conversation state is set to RESET.  
  
 This code may be returned through a verb issued after [MC_ALLOCATE](../core/mc-allocate.md).  
  
 AP_ALLOCATION_FAILURE_NO_RETRY  
  
 Secondary return code; the conversation cannot be allocated because of a permanent condition, such as a configuration error or session protocol error. To determine the error, the system administrator should examine the error log file. Do not retry the allocation until the error has been corrected.  
  
 AP_ALLOCATION_FAILURE_RETRY  
  
 Secondary return code; the conversation could not be allocated because of a temporary condition, such as a link failure. The reason for the failure is logged in the system error log. Retry the allocation.  
  
 AP_CONVERSATION_TYPE_MISMATCH  
  
 Secondary return code; the partner logical unit (LU) or TP does not support the conversation type (basic or mapped) specified in the allocation request.  
  
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
  
-   The node used by this conversation encountered an ABEND.  
  
-   The connection between the TP and the PU 2.1 node has been broken (a LAN error).  
  
-   The SnaBase at the TP's computer encountered an ABEND.  
  
 The system administrator should examine the error log to determine the reason for the ABEND.  
  
 AP_CONV_FAILURE_NO_RETRY  
 Primary return code; the conversation was terminated because of a permanent condition, such as a session protocol error. The system administrator should examine the system error log to determine the cause of the error. Do not retry the conversation until the error has been corrected.  
  
 AP_CONV_FAILURE_RETRY  
 Primary return code; the conversation was terminated because of a temporary error. Restart the TP to see if the problem occurs again. If it does, the system administrator should examine the error log to determine the cause of the error.  
  
 AP_CONVERSATION_TYPE_MIXED  
 Primary return code; the TP has issued both basic and mapped conversation verbs. Only one type can be issued in a single conversation.  
  
 AP_INVALID_VERB_SEGMENT  
 Primary return code; the VCB extended beyond the end of the data segment.  
  
 AP_PROG_ERROR_NO_TRUNC  
 Primary return code; the partner TP has issued [MC_SEND_ERROR](../core/mc-send-error.md) while the conversation was in SEND state. Data was not truncated.  
  
 AP_PROG_ERROR_PURGING  
 Primary return code; while in RECEIVE, PENDING, PENDING_POST, CONFIRM, CONFIRM_SEND, or CONFIRM_DEALLOCATE state, the partner TP issued **MC_SEND_ERROR**. Data sent but not yet received is purged.  
  
 AP_STACK_TOO_SMALL  
 Primary return code; the stack size of the application is too small to execute the verb. Increase the stack size of your application.  
  
 AP_CONV_BUSY  
 Primary return code; there can only be one outstanding conversation verb at a time on any conversation. This can occur if the local TP has multiple threads, and more than one thread is issuing APPC calls using the same **conv_id**.  
  
 AP_THREAD_BLOCKING  
 Primary return code; the calling thread is already in a blocking call.  
  
 AP_UNEXPECTED_DOS_ERROR  
 Primary return code; the operating system has returned an error to APPC while processing an APPC call from the local TP. The operating system return code is returned through the **secondary_rc**. It appears in Intel byte-swapped order. If the problem persists, consult the system administrator.  
  
 AP_DEALLOC_ABEND  
 Primary return code; the conversation has been deallocated for one of the following reasons:  
  
-   The partner TP issued [MC_DEALLOCATE](../core/mc-deallocate.md) with **dealloc_type** set to AP_ABEND.  
  
-   The partner TP encountered an ABEND, causing the partner LU to send an **MC_DEALLOCATE** request.  
  
## Remarks  
 The local TP receives data through the following process:  
  
1.  The local TP issues a receive verb until it finishes receiving a complete unit of data. The data received is one data record.  
  
     The local TP may need to issue the receive verb several times in order to receive a complete unit of data. After a complete unit of data has been received, the local TP can manipulate it.  
  
     The receive verbs are [MC_RECEIVE_AND_POST](../core/mc-receive-and-post.md), **MC_RECEIVE_AND_WAIT**, and [MC_RECEIVE_IMMEDIATE](../core/mc-receive-immediate.md).  
  
2.  The local TP issues the receive verb again. This has one of the following effects:  
  
    -   If the partner TP has sent more data, the local TP begins to receive a new unit of data.  
  
    -   If the partner TP has finished sending data or is waiting for confirmation, status information (available through the **what_rcvd** parameter) indicates the next action the local TP normally takes.  
  
 The conversation must be in RECEIVE or SEND state when the TP issues this verb.  
  
 **Issuing the Verb in SEND State**  
  
 Issuing **MC_RECEIVE_AND_WAIT** while the conversation is in SEND state has the following effects:  
  
-   The local LU sends the information in its send buffer and a SEND indicator to the partner TP.  
  
-   The conversation changes to RECEIVE state; the local TP waits for the partner TP to send data.  
  
 **State Change**  
  
 The new conversation state is determined by the following factors:  
  
-   The state the conversation is in when the TP issues the verb.  
  
-   The **primary_rc** parameter.  
  
-   The **what_rcvd** parameter if **primary_rc** contains AP_OK.  
  
 **Verb Issued in SEND State**  
  
 The following table details the state changes when **MC_RECEIVE_AND_WAIT** is issued in SEND state and **primary_rc** is AP_OK.  
  
|what_rcvd|New state|  
|----------------|---------------|  
|AP_CONFIRM_DEALLOCATE|CONFIRM_DEALLOCATE|  
|AP_DATA_COMPLETE_CONFIRM_DEALL|CONFIRM_DEALLOCATE|  
|AP_DATA_CONFIRM_DEALLOCATE|CONFIRM_DEALLOCATE|  
|AP_CONFIRM_SEND|CONFIRM_SEND|  
|AP_DATA_COMPLETE_CONFIRM_SEND|CONFIRM_SEND|  
|AP_DATA_CONFIRM_SEND|CONFIRM_SEND|  
|AP_CONFIRM_WHAT_RECEIVED|CONFIRM|  
|AP_DATA_COMPLETE_CONFIRM|CONFIRM|  
|AP_DATA_CONFIRM|CONFIRM|  
|AP_DATA|RECEIVE|  
|AP_DATA_COMPLETE|RECEIVE|  
|AP_DATA_INCOMPLETE|RECEIVE|  
|AP_SEND|No change|  
|AP_DATA_COMPLETE_SEND|SEND_PENDING|  
  
 The following table details the state changes when **MC_RECEIVE_AND_WAIT** is issued in SEND state and **primary_rc** is not AP_OK.  
  
|primary_rc|New state|  
|-----------------|---------------|  
|AP_ALLOCATION_ERROR|RESET|  
|AP_CONV_FAILURE_RETRY|RESET|  
|AP_CONV_FAILURE_NO_RETRY|RESET|  
|AP_DEALLOC_ABEND|RESET|  
|AP_DEALLOC_ABEND_PROG|RESET|  
|AP_DEALLOC_ABEND_SVC|RESET|  
|AP_DEALLOC_ABEND_TIMER|RESET|  
|AP_DEALLOC_NORMAL|RESET|  
|AP_PROG_ERROR_PURGING|RECEIVE|  
|AP_PROG_ERROR_NO_TRUNC|RECEIVE|  
|AP_SVC_ERROR_PURGING|RECEIVE|  
|AP_SVC_ERROR_NO_TRUNC|RECEIVE|  
  
 **Verb Issued in RECEIVE State**  
  
 The following table details the state changes when **MC_RECEIVE_AND_WAIT** is issued in RECEIVE state and **primary_rc** is AP_OK.  
  
|what_rcvd|New state|  
|----------------|---------------|  
|AP_CONFIRM_DEALLOCATE|CONFIRM_DEALLOCATE|  
|AP_DATA_COMPLETE_CONFIRM_DEALL|CONFIRM_DEALLOCATE|  
|AP_DATA_CONFIRM_DEALLOCATE|CONFIRM_DEALLOCATE|  
|AP_CONFIRM_SEND|CONFIRM_SEND|  
|AP_DATA_COMPLETE_CONFIRM_SEND|CONFIRM_SEND|  
|AP_DATA_CONFIRM_SEND|CONFIRM_SEND|  
|AP_CONFIRM_WHAT_RECEIVED|CONFIRM|  
|AP_DATA_COMPLETE_CONFIRM|CONFIRM|  
|AP_DATA_CONFIRM|CONFIRM|  
|AP_DATA|No change|  
|AP_DATA_COMPLETE|No change|  
|AP_DATA_INCOMPLETE|No change|  
|AP_SEND|SEND|  
|AP_DATA_COMPLETE_SEND|SEND_PENDING|  
  
 The following table details the state changes when **MC_RECEIVE_AND_WAIT** is issued in RECEIVE state and **primary_rc** is not AP_OK.  
  
|primary_rc|New state|  
|-----------------|---------------|  
|AP_ALLOCATION_ERROR|RESET|  
|AP_CONV_FAILURE_RETRY|RESET|  
|AP_CONV_FAILURE_NO_RETRY|RESET|  
|AP_DEALLOC_ABEND|RESET|  
|AP_DEALLOC_ABEND_PROG|RESET|  
|AP_DEALLOC_ABEND_SVC|RESET|  
|AP_DEALLOC_ABEND_TIMER|RESET|  
|AP_DEALLOC_NORMAL|RESET|  
|AP_PROG_ERROR_PURGING|No change|  
|AP_PROG_ERROR_NO_TRUNC|No change|  
|AP_SVC_ERROR_PURGING|No change|  
|AP_SVC_ERROR_NO_TRUNC|No change|  
|AP_PROG_ERROR_TRUNC|No change|  
|AP_SVC_ERROR_TRUNC|No change|