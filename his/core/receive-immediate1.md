---
title: "RECEIVE_IMMEDIATE1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5402ba5e-1801-4393-a056-5a9f576b1645
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# RECEIVE_IMMEDIATE
The **RECEIVE_IMMEDIATE** verb receives any data currently available from the partner transaction program (TP). If no data is available, the local TP does not wait. To avoid blocking the conversation, the Microsoft Windows operating system can issue [RECEIVE_AND_WAIT](../core/receive-and-wait2.md) in conjunction with [WinAsyncAPPC](../core/winasyncappc1.md).  
  
 The following structure describes the verb control block used by the **RECEIVE_IMMEDIATE** verb.  
  
## Syntax  
  
```  
  
struct receive_immediate {  
    unsigned short      opcode;  
    unsigned char       opext;  
    unsigned char       reserv2;  
    unsigned short      primary_rc;  
    unsigned long       secondary_rc;  
    unsigned char       tp_id[8];  
    unsigned long       conv_id;  
    unsigned short      what_rcvd;  
    unsigned char       rtn_status;  
    unsigned char       fill;  
    unsigned char       rts_rcvd;  
    unsigned char       reserv4;  
    unsigned short      max_len;  
    unsigned short      dlen;  
    unsigned char FAR * dptr;  
    unsigned char       reserv5[5];  
};   
```  
  
## Members  
 *opcode*  
 Supplied parameter. Specifies the verb operation code, AP_B_RECEIVE_IMMEDIATE.  
  
 *opext*  
 Supplied parameter. Specifies the verb operation extension, AP_BASIC_CONVERSATION.  
  
 *reserv2*  
 A reserved field.  
  
 *primary_rc*  
 Returned parameter. Specifies the primary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 *secondary_rc*  
 Returned parameter. Specifies the secondary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 *tp_id*  
 Supplied parameter. Identifies the local TP. The value of this parameter is returned by [TP_STARTED](../core/tp-started2.md) in the invoking TP or by [RECEIVE_ALLOCATE](../core/receive-allocate1.md) in the invoked TP.  
  
 *conv_id*  
 Supplied parameter. Provides the conversation identifier. The value of this parameter is returned by [ALLOCATE](../core/allocate2.md) in the invoking TP or by **RECEIVE_ALLOCATE** in the invoked TP.  
  
 *what_rcvd*  
 Returned parameter. Contains information received with the incoming data.  Possible values are listed following the Members section.  
  
 *rtn_status*  
 Supplied parameter. Indicates whether both data and conversation status indicators should be returned within one API call.  
  
 Use AP_NO to specify that indicators should be returned individually on separate invocations of the verb.  
  
 Use AP_YES to specify that indicators should be returned together, provided both are available. Both can be returned when:  
  
- The receive buffer is large enough to hold all of the data that precedes the status indicator.  
  
- The **fill** parameter specifies either BUFFER or LL, and the data is the last logical record before the status indicator.  
  
  *fill*  
  Supplied parameter. Specifies the manner in which the local TP receives data. It is used only for **RECEIVE_IMMEDIATE**.  
  
  Use AP_BUFFER to indicate that the local TP receives data until the number of bytes specified by **max_len** is reached or until end of data. Data is received without regard for the logical-record format.  
  
  Use AP_LL to indicate that data is received in logical-record format. The data received can be a complete logical record, a **max_len** byte portion of a logical record, or the end of a logical record.  
  
  *rts_rcvd*  
  Returned parameter. Contains the request-to-send indicator. Possible values are:  
  
- AP_YES indicates that the partner TP has issued [REQUEST_TO_SEND](../core/request-to-send1.md), which requests that the local TP change the conversation to RECEIVE state.  
  
- AP_NO indicates that the partner TP has not issued **REQUEST_TO_SEND**.  
  
  *max_len*  
  Supplied parameter. Indicates the maximum number of bytes of data the local TP can receive. The range is from 0 through 65535.  
  
  For the Windows operating system, this value must not exceed the length of the buffer to contain the received data.  
  
  By issuing **RECEIVE_IMMEDIATE** with **max_len** set to zero, the local TP can determine whether the partner TP has data to send, seeks confirmation, or has changed the conversation state.  
  
  *dlen*  
  Returned parameter. Provides the number of bytes of data received. Data is stored in a buffer specified by **dptr**. A length of zero indicates that no data was received.  
  
  *dptr*  
  Supplied parameter. Address of the buffer to contain the data received by the local TP.  
  
  For the Windows operating system, the data buffer can reside in a static data area or in a globally allocated area. The data buffer must fit entirely within this area.  
  
  **Values Returned by the what_rcvd Parameter**  
  
- AP_CONFIRM_DEALLOCATE indicates that the partner TP has issued [DEALLOCATE](../core/deallocate2.md) with **dealloc_type** set to AP_SYNC_LEVEL, and the conversation's synchronization level, established by **ALLOCATE**, is AP_CONFIRM_SYNC_LEVEL. Upon receiving this value, the local TP normally issues [CONFIRMED](../core/confirmed1.md).  
  
- AP_CONFIRM_SEND indicates that the partner TP has issued [PREPARE_TO_RECEIVE](../core/prepare-to-receive2.md) with **ptr_type** set to AP_SYNC_LEVEL, and the conversation's synchronization level, established by **ALLOCATE**, is AP_CONFIRM_SYNC_LEVEL. Upon receiving this value, the local TP normally issues **CONFIRMED**, and begins to send data.  
  
- AP_CONFIRM_WHAT_RECEIVED indicates that the partner TP has issued [CONFIRM](../core/confirm2.md). Upon receiving this value, the local TP normally issues **CONFIRMED**.  
  
- AP_DATA is returned for basic conversations by **RECEIVE_IMMEDIATE** if **fill** is set to AP_BUFFER. The local TP received data until **max_len** or end of data was reached. For more information, see "RECEIVE_IMMEDIATE End of Data" at the end of this topic.  
  
- AP_DATA_COMPLETE indicates, for **RECEIVE_IMMEDIATE** with **fill** set to AP_LL in basic conversations, that the local TP has received a complete logical record or the end of a logical record.  
  
   Upon receiving this value, the local TP normally reissues **RECEIVE_IMMEDIATE** or issues another receive verb. If the partner TP has sent more data, the local TP begins to receive a new unit of data.  
  
   Otherwise, the local TP examines status information if **primary_rc** contains AP_OK and **what_rcvd** contains any of these values:  
  
   AP_SEND  
  
   AP_CONFIRM_SEND  
  
   AP_CONFIRM_DEALLOCATE  
  
   AP_CONFIRM_WHAT_RECEIVED  
  
   See the description of the value in Return Codes in this topic for the next action the local TP normally takes.  
  
   If **primary_rc** contains AP_DEALLOC_NORMAL, the conversation has been deallocated in response to [DEALLOCATE](../core/deallocate2.md) issued by the partner TP.  
  
- AP_DATA_INCOMPLETE indicates for **RECEIVE_IMMEDIATE** in mapped conversations that the local TP has received an incomplete data record. The **max_len** parameter specified a value less than the length of the data record (or less than the remainder of the data record if this is not the first receive verb to read the record).  
  
   For **RECEIVE_IMMEDIATE** with **fill** set to AP_LL in basic conversations, this value indicates that the local TP has received an incomplete logical record.  
  
   Upon receiving this value, the local TP normally reissues RECEIVE_IMMEDIATE (or issues another receive verb) to receive the next part of the record.  
  
- AP_NONE indicates that the TP did not receive data or conversation status indicators.  
  
- AP_SEND indicates, for the partner TP, the conversation has entered RECEIVE state. For the local TP, the conversation is now in SEND state. Upon receiving this value, the local TP normally uses [SEND_DATA](../core/send-data1.md)to begin sending data.  
  
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
  
 AP_DATA_SEND  
 Primary return code; this is a combination of AP_DATA and AP_SEND.  
  
 AP_DATA_CONFIRM_SEND  
 Primary return code; this is a combination of AP_DATA and AP_CONFIRM_SEND.  
  
 AP_DATA_CONFIRM  
 Primary return code; this is a combination of AP_DATA and AP_CONFIRM_WHAT_RECEIVED.  
  
 AP_DATA_CONFIRM_DEALLOCATE  
 Primary return code; this is a combination of AP_DATA and AP_CONFIRM_DEALLOCATE.  
  
 AP_UNSUCCESSFUL  
 Primary return code; no data is immediately available from the partner TP.  
  
 AP_DEALLOC_NORMAL  
 Primary return code; the partner TP has deallocated the conversation without requesting confirmation. The partner TP issued [DEALLOCATE](../core/deallocate2.md) with **dealloc_type** set to one of the following:  
  
- AP_FLUSH  
  
- AP_SYNC_LEVEL with the synchronization level of the conversation specified as AP_NONE  
  
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
  
  AP_RCV_IMMD_BAD_FILL  
  
  Secondary return code for a basic conversation; the **fill** parameter was set to an invalid value.  
  
  AP_STATE_CHECK  
  Primary return code; the verb did not execute because it was issued in an invalid state.  
  
  AP_RCV_IMMD_BAD_STATE  
  
  Secondary return code; the conversation was not in RECEIVE state.  
  
  AP_ALLOCATION_ERROR  
  
  Secondary return code; APPC has failed to allocate a conversation. The conversation state is set to RESET.  
  
  This code may be returned through a verb issued after [ALLOCATE](../core/allocate2.md).  
  
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
  
- The node used by this conversation encountered an ABEND.  
  
- The connection between the TP and the PU 2.1 node has been broken (a LAN error).  
  
- The SnaBase at the TP's computer encountered an ABEND.  
  
  The system administrator should examine the error log to determine the reason for the ABEND.  
  
  AP_COMM_SUBSYSTEM_NOT_LOADED  
  Primary return code; a required component could not be loaded or has terminated while processing the verb. Thus, communication could not take place. Contact the system administrator for corrective action.  
  
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
  
  AP_PROG_ERROR_NO_TRUNC  
  Primary return code; the partner TP has issued [SEND_ERROR](../core/send-error2.md) with **err_type** set to AP_PROG while the conversation was in SEND state. Data was not truncated.  
  
  AP_PROG_ERROR_PURGING  
  Primary return code; while in RECEIVE, PENDING, PENDING_POST, CONFIRM, CONFIRM_SEND, or CONFIRM_DEALLOCATE state, the partner TP issued **SEND_ERROR** with **err_type** set to AP_PROG. Data sent but not yet received is purged.  
  
  AP_PROG_ERROR_TRUNC  
  Primary return code; in SEND state, after sending an incomplete logical record, the partner TP issued **SEND_ERROR** with **err_type** set to AP_PROG. The local TP may have received the first part of the logical record through a receive verb.  
  
  AP_STACK_TOO_SMALL  
  Primary return code; the stack size of the application is too small to execute the verb. Increase the stack size of your application.  
  
  AP_CONV_BUSY  
  Primary return code; there can only be one outstanding conversation verb at a time on any conversation. This can occur if the local TP has multiple threads, and more than one thread is issuing APPC calls using the same **conv_id**.  
  
  AP_UNEXPECTED_DOS_ERROR  
  Primary return code; the operating system has returned an error to APPC while processing an APPC call from the local TP. The operating system return code is returned through the **secondary_rc**. It appears in Intel byte-swapped order. If the problem persists, consult the system administrator.  
  
  AP_DEALLOC_ABEND_PROG  
  Primary return code; the conversation has been deallocated for one of the following reasons:  
  
- The partner TP has issued [DEALLOCATE](../core/deallocate2.md) with **dealloc_type** set to AP_ABEND_PROG.  
  
- The partner TP has encountered an ABEND, causing the partner LU to send a **DEALLOCATE** request.  
  
  AP_DEALLOC_ABEND_SVC  
  Primary return code; the conversation has been deallocated because the partner TP issued **DEALLOCATE** with **dealloc_type** set to AP_ABEND_SVC.  
  
  AP_DEALLOC_ABEND_TIMER  
  Primary return code; the conversation has been deallocated because the partner TP issued **DEALLOCATE** with **dealloc_type** set to AP_ABEND_TIMER.  
  
  AP_SVC_ERROR_NO_TRUNC  
  Primary return code; while in SEND state, the partner TP (or partner LU) issued **SEND_ERROR** with **err_type** set to AP_SVC. Data was not truncated.  
  
  AP_SVC_ERROR_PURGING  
  Primary return code; the partner TP (or partner LU) issued **SEND_ERROR** with **err_type** set to AP_SVC while in RECEIVE, PENDING_POST, CONFIRM, CONFIRM_SEND, or CONFIRM_DEALLOCATE state. Data sent to the partner TP may have been purged.  
  
  AP_SVC_ERROR_TRUNC  
  Primary return code; in SEND state, after sending an incomplete logical record, the partner TP (or partner LU) issued **SEND_ERROR**. The local TP may have received the first part of the logical record.  
  
## Remarks  
 The local TP receives data through the following process:  
  
1. The local TP issues a receive verb until it finishes receiving a complete unit of data. The data received can be:  
  
   - One logical record.  
  
   - A buffer of data received independent of its logical-record format.  
  
     The local TP may need to issue the receive verb several times in order to receive a complete unit of data. After a complete unit of data has been received, the local TP can manipulate it.  
  
     The receive verbs are [RECEIVE_AND_POST](../core/receive-and-post1.md), [RECEIVE_AND_WAIT](../core/receive-and-wait2.md), and **RECEIVE_IMMEDIATE**.  
  
2. The local TP issues the receive verb again. This has one of the following effects:  
  
   -   If the partner TP has sent more data, the local TP begins to receive a new unit of data.  
  
   -   If the partner TP has finished sending data or is waiting for confirmation, status information (available through **what_rcvd**) indicates the next action the local TP normally takes.  
  
   The conversation must be in RECEIVE state when the TP issues this verb.  
  
   The new state is determined by **primary_rc**. If **primary_rc** is AP_OK, the new state is determined by **what_rcvd**.  
  
   The following table details the state changes when the **primary_rc** is AP_OK.  
  
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
  
 The following table details the state changes when the **primary_rc** is not AP_OK.  
  
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
|AP_UNSUCCESSFUL|No change|  
  
## RECEIVE IMMEDIATE End of Data  
 In basic conversations, if the local TP issues **RECEIVE_IMMEDIATE** and sets **fill** to AP_BUFFER, the receipt of the data ends when **max_len** or the end of the data is reached. The end of the data is indicated by either:  
  
- A **primary_rc** parameter with a value other than AP_OK (for example, AP_DEALLOC_NORMAL).  
  
- A **what_rcvd** parameter with one of the following values:  
  
   AP_SEND  
  
   AP_CONFIRM_SEND  
  
   AP_CONFIRM_DEALLOCATE  
  
   AP_CONFIRM_WHAT_RECEIVED  
  
   AP_DATA_CONFIRM_SEND  
  
   AP_DATA_CONFIRM_DEALLOCATE  
  
   AP_DATA_CONFIRM  
  
  To determine if the end of the data has been reached, the local TP reissues **RECEIVE_IMMEDIATE**. If the new **primary_rc** parameter contains AP_OK and **what_rcvd** contains AP_DATA, the end of the data has not been reached. If, however, the end of the data has been reached, **primary_rc** or **what_rcvd** will indicate the cause of the end of the data.