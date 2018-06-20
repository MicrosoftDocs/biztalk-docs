---
title: "SEND_ERROR2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 790ebf6e-02b6-406b-95af-5350542c210c
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# SEND_ERROR
The **SEND_ERROR** verb notifies the partner transaction program (TP) that the local TP has encountered an application-level error.  
  
 The following structure describes the verb control block (VCB) used by the **SEND_ERROR** verb.  
  
## Syntax  
  
```  
  
struct send_error {  
    unsigned short      opcode;  
    unsigned char       opext;  
    unsigned char       reserv2;  
    unsigned short      primary_rc;  
    unsigned long       secondary_rc;  
    unsigned char       tp_id[8];  
    unsigned long       conv_id;  
    unsigned char       rts_rcvd;  
    unsigned char       err_type;  
    unsigned char       err_dir;  
    unsigned char       reserv3;  
    unsigned short      log_dlen;  
    unsigned char FAR * log_dptr;  
};   
```  
  
## Members  
 *opcode*  
 Supplied parameter. Specifies the verb operation code, AP_B_SEND_ERROR.  
  
 *opext*  
 Supplied parameter. Specifies the verb operation extension, AP_BASIC_CONVERSATION.  
  
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
 Supplied parameter. Provides the conversation identifier. The value of this parameter is returned by [ALLOCATE](../core/allocate2.md)in the invoking TP or by **RECEIVE_ALLOCATE** in the invoked TP.  
  
 *rts_rcvd*  
 Returned parameter. Indicates whether the partner TP issued [REQUEST_TO_SEND](../core/request-to-send1.md).Possible values include:  
  
- AP_YES indicates that the partner TP has issued **REQUEST_TO_SEND**, which requests that the local TP change the conversation to RECEIVE state. To change to RECEIVE state, the local TP can use [PREPARE_TO_RECEIVE](../core/prepare-to-receive2.md), [RECEIVE_AND_WAIT](../core/receive-and-wait2.md), or [RECEIVE_AND_POST](../core/receive-and-post1.md).  
  
- AP_NO indicates that the partner TP has not issued **REQUEST_TO_SEND**.  
  
  *err_type*  
  Supplied parameter. Indicates the type of the error being reported—application program or service program.  
  
  AP_PROG indicates that the error is to be reported to an end-user application program. This value causes APPC to send one of the following return codes to the partner TP:  
  
  AP_PROG_ERROR_NO_TRUNC  
  
  AP_PROG_ERROR_PURGING  
  
  AP_PROG_ERROR_TRUNC  
  
  AP_SVC indicates that the error is to be reported to a service program. This value causes APPC to send one of the following return codes to the partner TP:  
  
  AP_SVC_ERROR_NO_TRUNC  
  
  AP_SVC_ERROR_PURGING  
  
  AP_SVC_ERROR_TRUNC  
  
  *err_dir*  
  Supplied parameter. Indicates whether the error is with data just received or with data that is about to be sent. Use this parameter only when the conversation is in SEND_PENDING state. The parameter is ignored otherwise. The following are allowed values:  
  
- AP_RCV_DIR_ERROR indicates that the TP issued **SEND_ERROR** after detecting an error associated with the data just received.  
  
- AP_SEND_DIR_ERROR indicates that the TP issued **SEND_ERROR** after detecting an error associated with data it was going to send. For example, the TP encountered an error while reading data from the disk drive.  
  
  *reserv3*  
  A reserved field.  
  
  *log_dlen*  
  Supplied parameter for basic conversations; specifies the number of bytes of data to be sent to the error log file. The range is from 0 through 32767.  
  
  A length of zero indicates that there is no error log data.  
  
  *log_dptr*  
  Supplied parameter for basic conversations; specifies the address of the data buffer containing error information. The data is sent to the local error log and to the partner logical unit (LU).  
  
  This parameter is used by **SEND_ERROR** if **log_dlen** is greater than zero.  
  
  For Microsoft Windows, the data buffer can reside in a static data area or in a globally allocated area. The data buffer must fit entirely within this area.  
  
  The TP must format the error data as a GDS error log variable. For more information, see your IBM SNA manual(s).  
  
## Return Codes  
 AP_OK  
 Primary return code; the verb executed successfully.  
  
 AP_PARAMETER_CHECK  
 Primary return code; the verb did not execute because of a parameter error.  
  
 AP_BAD_CONV_ID  
  
 Secondary return code; the value of **conv_id** did not match a conversation identifier assigned by APPC.  
  
 AP_BAD_TP_ID  
  
 Secondary return code; the value of **tp_id** did not match a TP identifier assigned by APPC.  
  
 AP_BAD_ERROR_DIRECTION  
  
 Secondary return code; the specified **err_dir** was not recognized by APPC.  
  
 AP_INVALID_DATA_SEGMENT  
  
 Secondary return code; the error data for the log file was longer than the segment allocated to contain the error data, or the address of the error data buffer was wrong.  
  
 AP_SEND_ERROR_BAD_TYPE  
  
 Secondary return code; the value of **err_type** was invalid.  
  
 AP_SEND_ERROR_LOG_LL_WRONG  
  
 Secondary return code; the LL field of the error log GDS variable did not match the actual length of the data.  
  
 The following return codes can be generated when **SEND_ERROR** is issued in any allowed state:  
  
 AP_COMM_SUBSYSTEM_ABENDED  
 Primary return code; indicates one of the following conditions:  
  
- The node used by this conversation encountered an ABEND.  
  
- The connection between the TP and the PU 2.1 node has been broken (a LAN error).  
  
- The SnaBase at the TP's computer encountered an ABEND.  
  
  The system administrator should examine the error log to determine the reason for the ABEND.  
  
  AP_COMM_SUBSYSTEM_NOT_LOADED  
  Primary return code; a required component could not be loaded or has terminated while processing the verb. Thus, communication could not take place. Contact the system administrator for corrective action.  
  
  When this return code is used with **ALLOCATE**, it may indicate that no communications system could be found to support the local LU. (For example, the local LU alias specified with **TP_STARTED** is incorrect or has not been configured.) Note that if **lu_alias** or **mode_name** is fewer than eight characters, you must ensure that these fields are filled with spaces to the right. This error is returned if these parameters are not filled with spaces, since there is no node available that can satisfy the **ALLOCATE** request.  
  
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
  
  AP_STACK_TOO_SMALL  
  Primary return code; the stack size of the application is too small to execute the verb. Increase the stack size of your application.  
  
  AP_CONV_BUSY  
  Primary return code; there can only be one outstanding conversation verb at a time on any conversation. This may occur if the local TP has multiple threads, and more than one thread is issuing APPC calls using the same **conv_id**.  
  
  AP_THREAD_BLOCKING  
  Primary return code; the calling thread is already in a blocking call.  
  
  AP_UNEXPECTED_DOS_ERROR  
  Primary return code; the operating system has returned an error to APPC while processing an APPC call from the local TP. The operating system return code is returned through the **secondary_rc**. It appears in Intel byte-swapped order. If the problem persists, consult the system administrator.  
  
  The following return codes can be generated only if **SEND_ERROR** is issued in SEND state:  
  
  AP_ALLOCATION_ERROR  
  Primary return code; APPC has failed to allocate a conversation. The conversation state is set to RESET.  
  
  This code may be returned through a verb issued after [ALLOCATE](../core/allocate2.md).  
  
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
  
  AP_PROG_ERROR_PURGING  
  Primary return code; while in RECEIVE, PENDING, PENDING_POST, CONFIRM, CONFIRM_SEND, or CONFIRM_DEALLOCATE state, the partner TP issued **SEND_ERROR** with **err_type** set to AP_PROG. Data sent but not yet received is purged.  
  
  The following return codes can be generated only if **SEND_ERROR** is issued in SEND state:  
  
  AP_DEALLOC_ABEND_PROG  
  Primary return code; the conversation has been deallocated for one of the following reasons:  
  
- The partner TP has issued [DEALLOCATE](../core/deallocate2.md) with **dealloc_type** set to AP_ABEND_PROG.  
  
- The partner TP has encountered an ABEND, causing the partner LU to send a **DEALLOCATE** request.  
  
  AP_DEALLOC_ABEND_SVC  
  Primary return code; the conversation has been deallocated because the partner TP issued **DEALLOCATE** with **dealloc_type** set to AP_ABEND_SVC.  
  
  AP_DEALLOC_ABEND_TIMER  
  Primary return code; the conversation has been deallocated because the partner TP issued **DEALLOCATE** with **dealloc_type** set to AP_ABEND_TIMER.  
  
  AP_SVC_ERROR_PURGING  
  Primary return code; the partner TP (or partner LU) issued **SEND_ERROR** with **err_type** set to AP_SVC while in RECEIVE, PENDING_POST, CONFIRM, CONFIRM_SEND, or CONFIRM_DEALLOCATE state. Data sent to the partner TP may have been purged.  
  
  The following return code can be generated only if **SEND_ERROR** is issued in RECEIVE state:  
  
  AP_DEALLOC_NORMAL  
  Primary return code; this return code does not indicate an error.  
  
  The partner TP issued [DEALLOCATE](../core/deallocate2.md) with **dealloc_type** set to one of the following:  
  
- AP_FLUSH  
  
- AP_SYNC_LEVEL with the synchronization level of the conversation specified as AP_NONE  
  
## Remarks  
 The conversation can be in any state except RESET when the TP issues this verb. The conversation state must be SEND_PENDING if **err_dir** is used.  
  
 The local TP sends the error notification immediately to the partner TP; it does not hold the information in the local LU's send buffer.  
  
 Upon successful execution of this verb, the conversation is in SEND state for the local TP and in RECEIVE state for the partner TP.  
  
 The new state is determined by **primary_rc**. Possible state changes are summarized in the following table.  
  
|primary_rc|New state|  
|-----------------|---------------|  
|AP_OK|SEND|  
|AP_ALLOCATION_ERROR|RESET|  
|AP_CONV_FAILURE_RETRY|RESET|  
|AP_CONV_FAILURE_NO_RETRY|RESET|  
|AP_DEALLOC_ABEND|RESET|  
|AP_DEALLOC_ABEND_PROG|RESET|  
|AP_DEALLOC_ABEND_SVC|RESET|  
|AP_DEALLOC_ABEND_TIMER|RESET|  
|AP_DEALLOC_NORMAL|RESET|  
|AP_PROG_ERROR_PURGING|RECEIVE|  
|AP_SVC_ERROR_PURGING|RECEIVE|  
  
 If the conversation is in RECEIVE state when the TP issues **SEND_ERROR**, incoming data is purged by APPC. This data includes:  
  
- Data sent by [SEND_DATA](../core/send-data1.md).  
  
- Return code indicators.  
  
- Confirmation requests.  
  
- Deallocation requests.  
  
  APPC does not purge an incoming request-to-send indicator. APPC replaces purged incoming return code indicators with other return codes. The primary return code AP_OK replaces the following purged return code indicators:  
  
  AP_PROG_ERROR_NO_TRUNC  
  
  AP_PROG_ERROR_PURGING  
  
  AP_PROG_ERROR_TRUNC  
  
  AP_SVC_ERROR_NO_TRUNC  
  
  AP_SVC_ERROR_PURGING  
  
  AP_SVC_ERROR_TRUNC  
  
  The primary return code AP_DEALLOC_NORMAL replaces the following purged return code indicators:  
  
  AP_ALLOCATION_ERROR  
  
  AP_ALLOCATION_FAILURE_NO_RETRY  
  
  AP_ALLOCATION_FAILURE_RETRY  
  
  AP_CONVERSATION_TYPE_MISMATCH  
  
  AP_DEALLOC_ABEND  
  
  AP_DEALLOC_ABEND_PROG  
  
  AP_DEALLOC_ABEND_SVC  
  
  AP_DEALLOC_ABEND_TIMER  
  
  AP_PIP_NOT_ALLOWED  
  
  AP_PIP_NOT_SPECIFIED_CORRECTLY  
  
  AP_SECURITY_NOT_VALID  
  
  AP_SYNC_LEVEL_NOT_SUPPORTED  
  
  AP_TP_NAME_NOT_RECOGNIZED  
  
  AP_TRANS_PGM_NOT_AVAIL_NO_RETRY  
  
  AP_TRANS_PGM_NOT_AVAIL_RETRY  
  
  When the conversation is in SEND_PENDING state, APPC reports the following return codes to the partner TP based on the value in **err_dir**:  
  
  AP_PROG_ERROR_PURGING  
  The local TP issued **SEND_ERROR** with RECEIVE as the **err_dir**.  
  
  AP_PROG_ERROR_NO_TRUNC  
  The local TP issued **SEND_ERROR** with SEND as the **err_dir**.  
  
  AP_SVC_ERROR_PURGING  
  The local TP issued **SEND_ERROR** with RECEIVE as the **err_dir.**  
  
  AP_SVC_ERROR_NO_TRUNC  
  The local TP issued **SEND_ERROR** with SEND as the **err_dir**.