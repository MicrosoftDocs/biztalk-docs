---
title: "MC_DEALLOCATE2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 16d523e1-0109-4e71-ae8f-5090b4dbaf58
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# MC_DEALLOCATE
The **MC_DEALLOCATE** verb deallocates a conversation between two transaction programs (TP).  
  
 The following structure describes the verb control block (VCB) used by the **MC_DEALLOCATE** verb.  
  
## Syntax  
  
```  
  
struct mc_deallocate {  
    unsigned short   opcode;  
    unsigned char    opext;  
     unsigned char    reserv2;  
    unsigned short   primary_rc;  
    unsigned long    secondary_rc;  
    unsigned char    tp_id[8];  
    unsigned long    conv_id;  
    unsigned char    reserv3;  
    unsigned char    dealloc_type;  
    unsigned char    reserv4[2];  
    unsigned char    reserv5[4];  
    void             (WINAPI *callback)();  
    void             *correlator;  
    unsigned char    reserv6[4];  
};  
```  
  
## Members  
 *opcode*  
 Supplied parameter. Specifies the verb operation code, AP_M_DEALLOCATE.  
  
 *opext*  
 Supplied parameter. Specifies the verb operation extension, AP_MAPPED_CONVERSATION.  
  
 *reserv2*  
 A reserved field.  
  
 *primary_rc*  
 Returned parameter. Specifies the primary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 *secondary_rc*  
 Returned parameter. Specifies the secondary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 *tp_id*  
 Supplied parameter. Identifies the local TP. The value of this parameter was returned by [TP_STARTED](../core/tp-started2.md) in the invoking TP or by [RECEIVE_ALLOCATE](../core/receive-allocate1.md) in the invoked TP.  
  
 *conv_id*  
 Supplied parameter. Identifies the conversation established between the two TPs. The value of this parameter is returned by [MC_ALLOCATE](../core/mc-allocate2.md) in the invoking TP or by **RECEIVE_ALLOCATE** in the invoked TP.  
  
 *reserv3*  
 A reserved field.  
  
 *dealloc_type*  
 Supplied parameter. Specifies how to perform the deallocation.  
  
 For **MC_DEALLOCATE**, use AP_ABEND to deallocate the conversation abnormally. If the conversation is in SEND state when the local TP issues **MC_DEALLOCATE**, APPC sends the contents of the local logical unit's (LU) send buffer to the partner TP before deallocating the conversation. If the conversation is in RECEIVE or PENDING_POST state, APPC purges any incoming data before deallocating the conversation.  
  
 A TP should specify AP_ABEND when it encounters an error preventing the successful completion of a transaction.  
  
 AP_FLUSH sends the contents of the local LU's send buffer to the partner TP before deallocating the conversation. This value is allowed only if the conversation is in SEND state.  
  
 AP_SYNC_LEVEL uses the conversation's synchronization level (established by [MC_ALLOCATE](../core/mc-allocate2.md)) to determine how to deallocate the conversation. This value is allowed only if the conversation is in SEND state.  
  
 If the synchronization level of the conversation is AP_NONE, APPC sends the contents of the local LU's send buffer to the partner TP before deallocating the conversation.  
  
 If the synchronization level is AP_CONFIRM_SYNC_LEVEL, APPC sends the contents of the local LU's send buffer and a confirmation request to the partner TP. Upon receiving confirmation from the partner TP, APPC deallocates the conversation. If, however, the partner TP reports an error, the conversation remains allocated.  
  
 *callback*  
 Supplied parameter. Only present if the AP_EXTD_VCB bit is set in the **opext** member indicating support for Sync Point. This parameter is the address of a user-supplied callback function. If this field is NULL, no notification will be provided.  
  
 The prototype of the callback routine is as follows:  
  
```  
void WINAPI callback_proc(  
    struct appc_hdr *vcb,  
    unsigned char tp_id[8],  
    unsigned long conv_id,  
    unsigned short type,  
    void *correlator  
   );  
```  
  
 The callback procedure can take any name, since the address of the procedure is passed to the APPC DLL. The parameters passed to the function are as follows:  
  
 vcb  
  
 A pointer to the **MC_DEALLOCATE** verb control block that caused the conversation to be deallocated.  
  
 tp_id  
  
 The TP identifier of the TP that owned the deallocated conversation.  
  
 conv_id  
  
 The conversation identifier of the deallocated conversation.  
  
 type  
  
 The type of the message flow that caused the callback to be invoked. Possible values are:  
  
 AP_DATA_FLOW  
  
 Normal data flow on the session.  
  
 AP_UNBIND  
  
 The session was unbound normally.  
  
 AP_FAILURE  
  
 The session terminated due to an outage.  
  
 correlator  
  
 This value is the **correlator** specified on the **MC_DEALLOCATE** verb.  
  
 *correlator*  
 Supplied parameter. Only present if the AP_EXTD_VCB bit is set in the **opext** member indicating support for the Sync Point API. This **correlator** field allows the TP to specify a value it can use to correlate a call to the callback function with, for example, its own internal data structures. This value is returned to the TP as one of the parameters of the callback routine when it is invoked.  
  
 *reserv4*  
 A reserved field.  
  
## Return Codes  
 AP_OK  
 Primary return code; the verb executed successfully.  
  
 AP_PARAMETER_CHECK  
 Primary return code; the verb did not execute because of a parameter error.  
  
 AP_BAD_CONV_ID  
  
 Secondary return code; the value of **conv_id** did not match a conversation identifier assigned by APPC.  
  
 AP_BAD_TP_ID  
  
 Secondary return code; the value of **tp_id** did not match a TP identifier assigned by APPC.  
  
 AP_DEALLOC_BAD_TYPE  
  
 Secondary return code; the **dealloc_type** parameter was not set to a valid value.  
  
 AP_STATE_CHECK  
 Primary return code; the verb did not execute because it was issued in an invalid state.  
  
 AP_DEALLOC_CONFIRM_BAD_STATE  
  
 Secondary return code; the conversation was not in SEND state, and the TP attempted to flush the send buffer and send a confirmation request. This attempt occurred because the value of **dealloc_type** was AP_SYNC_LEVEL and the synchronization level of the conversation was AP_CONFIRM_SYNC_LEVEL.  
  
 AP_DEALLOC_FLUSH_BAD_STATE  
  
 Secondary return code; the conversation was not in SEND state and the TP attempted to flush the send buffer. This attempt occurred because the value of **dealloc_type** was AP_FLUSH or because the value of **dealloc_type** was AP_SYNC_LEVEL and the synchronization level of the conversation was AP_NONE. In either case, the conversation must be in SEND state.  
  
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
  
  AP_CONV_FAILURE_NO_RETRY  
  Primary return code; the conversation was terminated because of a permanent condition, such as a session protocol error. The system administrator should examine the system error log to determine the cause of the error. Do not retry the conversation until the error has been corrected.  
  
  AP_CONV_FAILURE_RETRY  
  Primary return code; the conversation was terminated because of a temporary error. Restart the TP to see if the problem occurs again. If it does, the system administrator should examine the error log to determine the cause of the error.  
  
  AP_CONVERSATION_TYPE_MIXED  
  Primary return code; the TP has issued both basic and mapped conversation verbs. Only one type can be issued in a single conversation.  
  
  AP_INVALID_VERB_SEGMENT  
  Primary return code; the VCB extended beyond the end of the data segment.  
  
  AP_PROG_ERROR_PURGING  
  Primary return code; while in RECEIVE, PENDING, PENDING_POST, CONFIRM, CONFIRM_SEND, or CONFIRM_DEALLOCATE state, the partner TP issued [MC_SEND_ERROR](../core/mc-send-error2.md). Data sent but not yet received is purged.  
  
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
  
- The partner TP issued **MC_DEALLOCATE** with **dealloc_type** set to AP_ABEND.  
  
- The partner TP encountered an ABEND, causing the partner LU to send an **MC_DEALLOCATE** request.  
  
## Remarks  
 Depending on the value of the **dealloc_type** parameter, the conversation can be in one of the states indicated in the following table when the TP issues **MC_DEALLOCATE**.  
  
|Dealloc_type|Allowed state|  
|-------------------|-------------------|  
|AP_FLUSH|SEND|  
|AP_SYNC_LEVEL|SEND|  
|AP_ABEND|Any state except RESET|  
|AP_ABEND_PROG|Any state except RESET|  
|AP_ABEND_SVC|Any state except RESET|  
|AP_ABEND_TIMER|Any state except RESET|  
  
 State changes, summarized in the following table, are based on the value of the **primary_rc**.  
  
|Primary_rc|New state|  
|-----------------|---------------|  
|AP_OK|RESET|  
|AP_ALLOCATION_ERROR|RESET|  
|AP_CONV_FAILURE_RETRY|RESET|  
|AP_CONV_FAILURE_NO_RETRY|RESET|  
|AP_DEALLOC_ABEND|RESET|  
|AP_DEALLOC_ABEND_PROG|RESET|  
|AP_DEALLOC_ABEND_SVC|RESET|  
|AP_DEALLOC_ABEND_TIMER|RESET|  
|AP_PROG_ERROR_PURGING|RECEIVE|  
  
 Before deallocating the conversation, this verb performs the equivalent of one of the following:  
  
- [MC_FLUSH](../core/mc-flush1.md), by sending the contents of the local LU's send buffer to the partner LU (and TP).  
  
- [MC_CONFIRM](../core/mc-confirm2.md), by sending the contents of the local LU's send buffer and a confirmation request to the partner TP.  
  
  After this verb has successfully executed, the conversation identifier is no longer valid.  
  
  LU 6.2 Sync Point can use an optimization of the message flows known as implied forget. When the protocol specifies that a FORGET PS header is required, the next data flow on the session implies that a FORGET has been received. In the normal situation, the TP is aware of the next data flow when data is received or sent on one of its Sync Point conversations.  
  
  However, it is possible that the last message to flow is caused by the conversation being deallocated. In this case, the TP is unaware when the next data flow on the session occurs. In order to provide the TP with this notification, the **MC_DEALLOCATE** verb is modified to allow the TP to register a callback function which will be called:  
  
- On the first normal flow transmission (request or response) over the session used by the conversation.  
  
- If the session is unbound before any other data flows.  
  
- If the session is terminated abnormally due to a DLC outage.  
  
  The **MC_DEALLOCATE** verb also contains a **correlator** field member that is returned as one of the parameters when the callback function is invoked. The application can use this parameter in any way (for example, as a pointer to a control block within the application).  
  
  The TP can use the *type* parameter passed to the callback function to determine whether the message flow indicates an implied forget has been received.  
  
  Note that the **MC_DEALLOCATE** verb will probably complete before the callback routine is called. The conversation is considered to be in RESET state and no further verbs can be issued using the conversation identifier. If the application issues a [TP_ENDED](../core/tp-ended1.md) verb before the next data flow on the session, the callback routine will not be invoked.  
  
  Host Integration Server allows TPs to deallocate conversations immediately after sending data by specifying the type parameter on [MC_SEND_DATA](../core/mc-send-data1.md) as AP_SEND_DATA_DEALLOC_\*. However, the **MC_SEND_DATA** verbs do not contain the implied forget callback function. TPs wishing to receive implied forget notification must issue **MC_DEALLOCATE** explicitly.