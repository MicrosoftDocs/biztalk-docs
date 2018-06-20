---
title: "MC_SEND_DATA1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8dcab8be-cb3f-4b0c-b443-dc2fc695a1f6
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# MC_SEND_DATA
The **MC_SEND_DATA** verb places data in the local logical unit's (LU) send buffer for transmission to the partner transaction program (TP).  
  
 The following structure describes the verb control block (VCB) used by the **MC_SEND_DATA** verb.  
  
## Syntax  
  
```  
  
struct mc_send_data {  
    unsigned short      opcode;  
    unsigned char       opext;  
    unsigned char       reserv2;  
    unsigned short      primary_rc;  
    unsigned long       secondary_rc;  
    unsigned char       tp_id[8];  
    unsigned long       conv_id;  
    unsigned char       rts_rcvd;  
    unsigned char       data_type;  
    unsigned short int  dlen;  
    unsigned char FAR * dptr ;  
    unsigned char       type;  
    unsigned char       reserv4;  
};   
```  
  
## Members  
 *opcode*  
 Supplied parameter. Specifies the verb operation code, AP_M_SEND_DATA.  
  
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
  
 The value of this parameter is returned by [TP_STARTED](../core/tp-started2.md) in the invoking TP or by [RECEIVE_ALLOCATE](../core/receive-allocate1.md) in the invoked TP.  
  
 *conv_id*  
 Supplied parameter. Provides the conversation identifier.  
  
 The value of this parameter is returned by [MC_ALLOCATE](../core/mc-allocate2.md) in the invoking TP or by **RECEIVE_ALLOCATE** in the invoked TP.  
  
 *rts_rcvd*  
 Returned parameter. Provides the request-to-send-received indicator.  
  
- AP_YES indicates that the partner TP has issued [MC_REQUEST_TO_SEND](../core/mc-request-to-send1.md), which requests that the local TP change the conversation to RECEIVE state. To change to RECEIVE state, the local TP can use [MC_PREPARE_TO_RECEIVE](../core/mc-prepare-to-receive1.md), [MC_RECEIVE_AND_WAIT](../core/mc-receive-and-wait2.md), or [MC_RECEIVE_AND_POST](../core/mc-receive-and-post2.md).  
  
- AP_NO indicates that the partner TP has not issued **MC_REQUEST_TO_SEND**.  
  
  *data_type*  
  Supplied parameter. Specifies the type of data to be sent if Sync Point is supported. Valid parameters are:  
  
  AP_APPLICATION  
  
  AP_USER_CONTROL_DATA  
  
  AP_PS_HEADER  
  
  *dlen*  
  Supplied parameter. Specifies the number of bytes of data to be put in the local LU's send buffer. The range is from 0 through 65535.  
  
  *dptr*  
  Supplied parameter. Specifies the address of the buffer containing the data to be put in the local LU's send buffer.  
  
  For the Windows operating system, the data buffer can reside in a static data area or in a globally allocated area. The data buffer must fit entirely within this area.  
  
  *type*  
  Supplied parameter. Allows a TP to send data and perform other functions within one API call. For example, you can combine **MC_SEND_DATA** with **type** set to CONFIRM to accomplish the same objective as issuing **MC_SEND_DATA** followed by [MC_CONFIRM](../core/mc-confirm2.md).  
  
- AP_SEND_DATA_CONFIRM corresponds to **MC_SEND_DATA** followed by **MC_CONFIRM**.  
  
- AP_SEND_DATA_FLUSH corresponds to **MC_SEND_DATA** followed by [MC_FLUSH](../core/mc-flush1.md).  
  
- AP_SEND_DATA_DEALLOC_ABEND corresponds to **MC_SEND_DATA** followed by [MC_DEALLOCATE](../core/mc-deallocate2.md) with a **dealloc_type** of AP_ABEND.  
  
- AP_SEND_DATA_DEALLOC_FLUSH corresponds to **MC_SEND_DATA** followed by **MC_DEALLOCATE** with a **dealloc_type** of AP_FLUSH.  
  
- AP_SEND_DATA_DEALLOC_SYNC_LEVEL corresponds to **MC_SEND_DATA** followed by **MC_DEALLOCATE** with a **dealloc_type** of AP_SYNC_LEVEL.  
  
- AP_SEND_DATA_P_TO_R_FLUSH corresponds to **MC_SEND_DATA** followed by [MC_PREPARE_TO_RECEIVE](../core/mc-prepare-to-receive1.md) with a **ptr_type** of AP_FLUSH.  
  
- AP_SEND_DATA_P_TO_R_SYNC_LEVEL corresponds to **MC_SEND_DATA** followed by **MC_PREPARE_TO_RECEIVE** with a **ptr_type** of AP_SYNC_LEVEL and **locks** set to AP_SHORT.  
  
## Return Codes  
 AP_OK  
 Primary return code; the verb executed successfully.  
  
 AP_PARAMETER_CHECK  
 Primary return code; the verb did not execute because of a parameter error.  
  
 AP_BAD_CONV_ID  
  
 Secondary return code; the value of **conv_id** did not match a conversation identifier assigned by APPC.  
  
 AP_BAD_TP_ID  
  
 Secondary return code; the value of **tp_id** did not match a TP identifier assigned by APPC.  
  
 AP_INVALID_DATA_SEGMENT  
  
 Secondary return code; the length specified for the data buffer was longer than the segment allocated to contain the buffer.  
  
 AP_SEND_DATA_INVALID_TYPE  
  
 Secondary return code; the specified type was not recognized by APPC.  
  
 AP_SEND_DATA_CONFIRM_SYNC_NONE  
  
 Secondary return code; the **type** CONFIRM is not permitted for a conversation that was allocated with a **sync_level** of NONE.  
  
 AP_STATE_CHECK  
 Primary return code; the verb did not execute because it was issued in an invalid state.  
  
 AP_SEND_DATA_NOT_SEND_STATE  
  
 Secondary return code; the local TP issued **MC_SEND_DATA**, but the conversation was not in SEND state.  
  
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
  Primary return code; a required component could not be loaded or has terminated while processing the verb. Thus, communication could not take place. Contact the system administrator for corrective action.  
  
  When this return code is used with [MC_ALLOCATE](../core/mc-allocate2.md), it may indicate that no communications system could be found to support the local LU. (For example, the local LU alias specified with [TP_STARTED](../core/tp-started2.md) is incorrect or has not been configured.) Note that if **lu_alias** or **mode_name** is fewer than eight characters, you must ensure that these fields are filled with spaces to the right. This error is returned if these parameters are not filled with spaces, since there is no node available that can satisfy the **MC_ALLOCATE** request.  
  
  When **MC_ALLOCATE** produces this return code for a Microsoft Host Integration Server Client system configured with multiple nodes, there are two secondary return codes as follows:  
  
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
  
- The partner TP issued [MC_DEALLOCATE](../core/mc-deallocate2.md) with **dealloc_type** set to AP_ABEND.  
  
- The partner TP encountered an ABEND, causing the partner LU to send an **MC_DEALLOCATE** request.  
  
## Remarks  
 The conversation must be in SEND state when the TP issues this verb. State changes, based on **primary_rc**, are summarized in the following table.  
  
|primary_rc|New state|  
|-----------------|---------------|  
|AP_OK|No change|  
|AP_ALLOCATION_ERROR|RESET|  
|AP_CONV_FAILURE_RETRY|RESET|  
|AP_CONV_FAILURE_NO_RETRY|RESET|  
|AP_DEALLOC_ABEND|RESET|  
|AP_DEALLOC_ABEND_PROG|RESET|  
|AP_DEALLOC_ABEND_SVC|RESET|  
|AP_DEALLOC_ABEND_TIMER|RESET|  
|AP_PROG_ERROR_PURGING|RECEIVE|  
|AP_SVC_ERROR_PURGING|RECEIVE|  
  
 **MC_SEND_DATA** may wait indefinitely because the partner TP has not issued a receive verb. If this occurs, the send buffer may fill up.  
  
 The data collected in the local LU's send buffer is transmitted to the partner LU (and partner TP) when one of the following occurs:  
  
-   The send buffer fills up.  
  
-   The local TP issues [MC_FLUSH](../core/mc-flush1.md), [MC_CONFIRM](../core/mc-confirm2.md), or [MC_DEALLOCATE](../core/mc-deallocate2.md) (or other verb that flushes the LU's send buffer).