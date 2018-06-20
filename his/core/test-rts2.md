---
title: "TEST_RTS2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c42e5292-3efa-4314-8e73-244f41d40b98
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# TEST_RTS
The **TEST_RTS** verb determines whether a request-to-send notification has been received from the partner transaction program (TP).  
  
 The following structure describes the verb control block (VCB) used by the **TEST_RTS** verb.  
  
## Syntax  
  
```  
  
struct test_rts {  
    unsigned short      opcode;  
    unsigned char       opext;  
    unsigned char       reserv2;  
    unsigned short      primary_rc;  
    unsigned long       secondary_rc;  
    unsigned char       tp_id[8];  
    unsigned long       conv_id;  
    unsigned char       reserv3;  
};  
```  
  
## Members  
 *opcode*  
 Supplied parameter. Specifies the verb operation code, AP_B_TEST_RTS.  
  
 *opext*  
 Supplied parameter. Specifies the verb operation extension, AP_BASIC_CONVERSATION.  
  
 *reserv2*  
 A reserved field.  
  
 *primary_rc*  
 Returned parameter. Specifies the primary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 *secondary_rc*  
 Returned parameter. Specifies the secondary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 *tp_id*  
 Supplied parameter. Identifies the local TP. The value of this parameter was returned by [TP_STARTED](../core/tp-started2.md) in the invoking TP or by [RECEIVE_ALLOCATE](../core/receive-allocate1.md) in the invoked TP.  
  
 *conv_id*  
 Supplied parameter. Provides the conversation identifier. The value of this parameter was returned by [ALLOCATE](../core/allocate2.md) in the invoking TP or by **RECEIVE_ALLOCATE** in the invoked TP.  
  
 *reserv3*  
 A reserved field.  
  
## Return Codes  
 AP_OK  
 Primary return code; the verb executed successfully.  
  
 AP_UNSUCCESSFUL  
 Primary return code; request-to-send notification has not been received.  
  
 AP_PARAMETER_CHECK  
 Primary return code; the verb did not execute because of a parameter error.  
  
 AP_BAD_CONV_ID  
  
 Secondary return code; the value of **conv_id** did not match a conversation identifier assigned by APPC.  
  
 AP_BAD_TP_ID  
 Secondary return code; the value of **tp_id** did not match a TP identifier assigned by APPC.  
  
 AP_COMM_SUBSYSTEM_ABENDED  
 Primary return code; indicates one of the following conditions:  
  
- The node used by this conversation encountered an ABEND.  
  
- The connection between the TP and the PU 2.1 node has been broken (a LAN error).  
  
- The SnaBase at the TP's computer encountered an ABEND.  
  
  The system administrator should examine the error log to determine the reason for the ABEND.  
  
  AP_COMM_SUBSYSTEM_NOT_LOADED  
  Primary return code; a required component could not be loaded or has terminated while processing the verb. Thus, communication could not take place. Contact the system administrator for corrective action.  
  
  When this return code is used with **ALLOCATE**, it may indicate that no communications system could be found to support the local logical unit (LU). (For example, the local LU alias specified with **TP_STARTED** is incorrect or has not been configured.) Note that if **lu_alias** or **mode_name** is fewer than eight characters, you must ensure that these fields are filled with spaces to the right. This error is returned if these parameters are not filled with spaces, since there is no node available that can satisfy the **ALLOCATE** request.  
  
  When **ALLOCATE** produces this return code for a Host Integration Server Client system configured with multiple nodes, there are two secondary return codes as follows:  
  
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
 The conversation can be in any state except RESET when the TP issues this verb.  
  
 There is no state change.