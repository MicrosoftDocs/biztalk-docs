---
title: "GET_STATE2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4d3f49cd-d227-4149-90a4-777510657307
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# GET_STATE
The **GET_STATE** verb returns the state of a particular conversation.  
  
 The following structure describes the verb control block (VCB) used by the **GET_STATE** verb.  
  
## Syntax  
  
```  
  
struct get_state {  
    unsigned short   opcode;  
    unsigned char    opext;  
    unsigned char    reserv2;  
    unsigned short   primary_rc;  
    unsigned long    secondary_rc;  
    unsigned char    tp_id[8];  
    unsigned long    conv_id;  
    unsigned char    conv_state;  
};   
```  
  
## Members  
 *opcode*  
 Supplied parameter. Specifies the verb operation code, AP_GET_STATE.  
  
 *opext*  
 This field is unused by the **GET_STATE** verb.  
  
 *reserv2*  
 A reserved field.  
  
 *primary_rc*  
 Returned parameter. Specifies the primary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 *secondary_rc*  
 Returned parameter. Specifies the secondary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 *tp_id*  
 Supplied parameter. Identifies the local transaction program (TP). The value of this parameter was returned by [TP_STARTED](../core/tp-started.md) in the invoking TP or by [RECEIVE_ALLOCATE](../core/receive-allocate.md) in the invoked TP.  
  
 *conv_id*  
 Supplied parameter. Provides the identifier for the conversation about which this TP is inquiring. The value of this parameter was returned by [MC_ALLOCATE](../core/mc-allocate.md) or [ALLOCATE](../core/allocate.md) in the invoking TP or by **RECEIVE_ALLOCATE** in the invoked TP.  
  
 *conv_state*  
 Returned parameter. Indicates the state of the conversation. The **conv_state** parameter can be one of the following values:  
  
 AP_RESET_STATE  
  
 The conversation is in the RESET state.  
  
 AP_SEND_STATE  
  
 The conversation is in the SEND state.  
  
 AP_RECEIVE_STATE  
  
 The conversation is in the RECEIVE state.  
  
 AP_CONFIRM_STATE  
  
 The conversation is in the CONFIRM state.  
  
 AP_CONFIRM_SEND_STATE  
  
 The conversation is in the CONFIRM_SEND state.  
  
 AP_CONFIRM_DEALL_STATE  
  
 The conversation is in the CONFIRM_DEALLOCATE state.  
  
 AP_PEND_POST_STATE  
  
 The conversation has a **POST** verb pending.  
  
 AP_PEND_DEALL_STATE  
  
 The conversation has a **DEALLOCATE** verb pending.  
  
 AP_END_CONV_STATE  
  
 The conversation is in the END_CONVERSATION state.  
  
 AP_SEND_PENDING_STATE  
  
 The conversation is in the SEND_PENDING state.  
  
## Return Codes  
 AP_OK  
 Primary return code; the verb executed successfully.  
  
 AP_PARAMETER_CHECK  
 Primary return code; the verb did not execute because of a parameter error.  
  
 AP_BAD_CONV_ID  
  
 Secondary return code; the value of **conv_id** did not match a conversation identifier assigned by APPC.  
  
 AP_BAD_TP_ID  
  
 Secondary return code; the value of **tp_id** did not match a TP identifier assigned by APPC.  
  
 AP_COMM_SUBSYSTEM_ABENDED  
 Primary return code; indicates one of the following conditions:  
  
-   The node used by this conversation encountered an ABEND.  
  
-   The connection between the TP and the PU 2.1 node has been broken (a LAN error).  
  
-   The SnaBase at the TP's computer encountered an ABEND.  
  
 The system administrator should examine the error log to determine the reason for the ABEND.  
  
 AP_INVALID_VERB_SEGMENT  
 Primary return code; the VCB extended beyond the end of the data segment.  
  
 AP_STACK_TOO_SMALL  
 Primary return code; the stack size of the application is too small to execute the verb. Increase the stack size of your application.  
  
 AP_CONV_BUSY  
 Primary return code; there can only be one outstanding conversation verb at a time on any conversation. This can occur if the local TP has multiple threads, and more than one thread is issuing APPC calls using the same **conv_id**.  
  
 AP_UNEXPECTED_DOS_ERROR  
 Primary return code; the operating system has returned an error to APPC while processing an APPC call from the local TP. The operating system return code is returned through the **secondary_rc**. It appears in Intel byte-swapped order. If the problem persists, consult the system administrator.  
  
## Remarks  
 The conversation can be in any state when the TP issues this verb.  
  
 There is no state change.