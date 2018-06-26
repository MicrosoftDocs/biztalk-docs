---
title: "REQUEST_TO_SEND1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dde56a43-0701-4112-b8f4-218e39ab4508
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# REQUEST_TO_SEND
The **REQUEST_TO_SEND** verb notifies the partner transaction program (TP) that the local TP wants to send data.  
  
 The following structure describes the verb control block (VCB) used by the **REQUEST_TO_SEND** verb.  
  
## Syntax  
  
```  
  
struct request_to_send {  
    unsigned short      opcode;  
    unsigned char       opext;  
    unsigned char       reserv2;  
    unsigned short      primary_rc;  
    unsigned long       secondary_rc;  
    unsigned char       tp_id[8];  
    unsigned long       conv_id;  
};   
```  
  
## Members  
 *opcode*  
 Supplied parameter. Specifies the verb operation code, AP_B_REQUEST_TO_SEND.  
  
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
 Supplied parameter. Provides the conversation identifier.  
  
 The value of this parameter is returned by [ALLOCATE](../core/allocate2.md) in the invoking TP or by **RECEIVE_ALLOCATE** in the invoked TP.  
  
## Return Codes  
 AP_OK  
 Primary return code; the verb executed successfully.  
  
 AP_PARAMETER_CHECK  
 Primary return code; the verb did not execute because of a parameter error.  
  
 AP_BAD_CONV_ID  
  
 Secondary return code; the value of **conv_id** did not match a conversation identifier assigned by APPC.  
  
 AP_BAD_TP_ID  
  
 Secondary return code; the value of **tp_id** did not match a TP identifier assigned by APPC.  
  
 AP_STATE_CHECK  
 Primary return code; the verb did not execute because it was issued in an invalid state.  
  
 AP_R_T_S_BAD_STATE  
  
 Secondary return code; the conversation is not in an allowed state when the TP issued this verb.  
  
 AP_COMM_SUBSYSTEM_ABENDED  
 Primary return code; indicates one of the following conditions:  
  
- The node used by this conversation encountered an ABEND.  
  
- The connection between the TP and the PU 2.1 node has been broken (a LAN error).  
  
- The SnaBase at the TP's computer encountered an ABEND.  
  
  The system administrator should examine the error log to determine the reason for the ABEND.  
  
  AP_COMM_SUBSYSTEM_NOT_LOADED  
  Primary return code; a required component could not be loaded or has terminated while processing the verb. Thus, communication could not take place. Contact the system administrator for corrective action.  
  
  When this return code is used with [ALLOCATE](../core/allocate2.md), it may indicate that no communications system could be found to support the local logical unit (LU). (For example, the local LU alias specified with [TP_STARTED](../core/tp-started2.md) is incorrect or has not been configured.) Note that if **lu_alias** or **mode_name** is fewer than eight characters, you must ensure that these fields are filled with spaces to the right. This error is returned if these parameters are not filled with spaces, since there is no node available that can satisfy the **ALLOCATE** request.  
  
  When **ALLOCATE** produces this return code for a Microsoft Host Integration Server Client system configured with multiple nodes, there are two secondary return codes as follows:  
  
  0xF0000001  
  
  Secondary return code; no nodes have been started.  
  
  0xF0000002  
  
  Secondary return code; at least one node has been started, but the local LU (when **TP_STARTED** is issued) is not configured on any active nodes. The problem could be either of the following:  
  
- The node with the local LU is not started.  
  
- The local LU is not configured.  
  
  AP_CONVERSATION_TYPE_MIXED  
  Primary return code; the TP has issued both basic and mapped conversation verbs. Only one type can be issued in a single conversation.  
  
  AP_INVALID_VERB_SEGMENT  
  Primary return code; the VCB extended beyond the end of the data segment.  
  
  AP_STACK_TOO_SMALL  
  Primary return code; the stack size of the application is too small to execute the verb. Increase the stack size of your application.  
  
  AP_CONV_BUSY  
  Primary return code; there can only be one outstanding conversation verb at a time on any conversation. This can occur if the local TP has multiple threads, and more than one thread is issuing APPC calls using the same **conv_id**.  
  
  AP_THREAD_BLOCKING  
  Primary return code; the calling thread is already in a blocking call.  
  
  AP_UNEXPECTED_DOS_ERROR  
  Primary return code; the operating system has returned an error to APPC while processing an APPC call from the local TP. The operating system return code is returned through the **secondary_rc**. It appears in Intel byte-swapped order. If the problem persists, consult the system administrator.  
  
## Remarks  
 The conversation can be in any of the following states when the TP issues this verb:  
  
 CONFIRM  
  
 PENDING_POST (OS/2)  
  
 RECEIVE  
  
 There is no state change.  
  
 The request-to-send notification is received by the partner program through the **rts_rcvd** parameter of the following verbs:  
  
- [CONFIRM](../core/confirm2.md)  
  
- [RECEIVE_AND_POST](../core/receive-and-post1.md)  
  
- [RECEIVE_AND_WAIT](../core/receive-and-wait2.md)  
  
- [RECEIVE_IMMEDIATE](../core/receive-immediate1.md)  
  
- [SEND_DATA](../core/send-data1.md)  
  
- [SEND_ERROR](../core/send-error2.md)  
  
  It is also indicated by a **primary_rc** of AP_OK on [TEST_RTS](../core/test-rts2.md).  
  
  Request-to-send notification is sent to the partner TP immediately; APPC does not wait until the send buffer fills up or is flushed. Consequently, the request-to-send notification may arrive out of sequence. For example, if the local TP is in SEND state and issues [PREPARE_TO_RECEIVE](../core/prepare-to-receive2.md) followed by **REQUEST_TO_SEND**, the partner TP, in RECEIVE state, may receive the request-to-send notification before it receives the send notification. For this reason, request-to-send can be reported to a TP through a receive verb.  
  
  In response to this request, the partner TP can change the conversation to:  
  
- RECEIVE state by issuing **PREPARE_TO_RECEIVE** or **RECEIVE_AND_WAIT**.  
  
- PENDING_POST state by issuing **RECEIVE_AND_POST**.  
  
  The partner TP can also ignore the request-to-send.  
  
  The conversation state changes to SEND for the local TP when the local TP receives one of the following values through the **what_rcvd** parameter of a subsequent receive verb:  
  
- AP_CONFIRM_SEND and replies with [CONFIRMED](../core/confirmed1.md)  
  
- AP_DATA_COMPLETE_CONFIRM_SEND and replies with **CONFIRMED**  
  
- AP_DATA_CONFIRM_SEND and replies with **CONFIRMED**  
  
- AP_SEND  
  
  The receive verbs are [RECEIVE_AND_POST](../core/receive-and-post1.md), [RECEIVE_IMMEDIATE](../core/receive-immediate1.md), and [RECEIVE_AND_WAIT](../core/receive-and-wait2.md).