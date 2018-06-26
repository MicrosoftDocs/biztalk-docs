---
title: "MC_CONFIRMED1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cb70416a-9f1c-400c-8756-37dafe114bec
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# MC_CONFIRMED
The **MC_CONFIRMED** verb responds to a confirmation request from the partner transaction program (TP). It informs the partner TP that the local TP has not detected an error in the received data. Because the TP issuing the confirmation request waits for a confirmation, **MC_CONFIRMED** synchronizes the processing of the two TPs.  

 The following structure describes the verb control block (VCB) used by the **MC_CONFIRMED** verb.  

## Syntax  

```  

struct mc_confirmed {  
    unsigned short  opcode;  
    unsigned char   opext;  
    unsigned char   reserv2;  
    unsigned short  primary_rc;  
    unsigned long   secondary_rc;  
    unsigned char   tp_id[8];  
    unsigned long   conv_id;  
    unsigned char   rts_rcvd;  
};   
```  

## Members  
 *opcode*  
 Supplied parameter. Specifies the verb operation code, AP_M_CONFIRMED.  

 *opext*  
 Supplied parameter. Specifies the verb operation extension, AP_MAPPED_CONVERSATION.  

 *reserv2*  
 A reserved field.  

 *primary_rc*  
 Returned parameter. Specifies the primary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  

 *secondary_rc*  
 Returned parameter. Specifies the secondary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  

 *tp_id*  
 Supplied parameter. Identifies the local TP. The value of this parameter was returned by [TP_STARTED](../core/tp-started2.md)in the invoking TP or by [RECEIVE_ALLOCATE](../core/receive-allocate1.md) in the invoked TP.  

 *conv_id*  
 Supplied parameter. Identifies the conversation established between the two TPs. The value of this parameter is returned by [MC_ALLOCATE](../core/mc-allocate2.md) in the invoking TP or by **RECEIVE_ALLOCATE** in the invoked TP.  

 *rts_rcvd*  
 Returned parameter. Indicates whether the partner TP issued [MC_REQUEST_TO_SEND](../core/mc-request-to-send1.md), which requests the local TP to change the conversation to RECEIVE state.  

 To change to RECEIVE state the local TP can use [MC_PREPARE_TO_RECEIVE](../core/mc-prepare-to-receive1.md), [MC_RECEIVE_AND_WAIT](../core/mc-receive-and-wait2.md), or [MC_RECEIVE_AND_POST](../core/mc-receive-and-post2.md).  

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

 AP_CONFIRMED_BAD_STATE  

 Secondary return code; the conversation is not in CONFIRM, CONFIRM_SEND, or CONFIRM_DEALLOCATE state.  

 AP_COMM_SUBSYSTEM_ABENDED  
 Primary return code; indicates one of the following conditions:  

- The node used by this conversation encountered an ABEND.  

- The connection between the TP and the PU 2.1 node has been broken (a LAN error).  

- The SnaBase at the TP's computer encountered an ABEND.  

  The system administrator should examine the error log to determine the reason for the ABEND.  

  AP_COMM_SUBSYSTEM_NOT_LOADED  
  Primary return code; a required component could not be loaded or terminated while processing the verb. Thus, communication could not take place. Contact the system administrator for corrective action.  

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
 The conversation must be in one of the following states when the TP issues this verb:  

- CONFIRM  

- CONFIRM_SEND  

- CONFIRM_DEALLOCATE  

  The new state is determined by the old state—the state of the conversation when the local TP issued **MC_CONFIRMED**. The old state is indicated by the value of the **what_rcvd** parameter of the preceding receive verb. The following state changes are possible:  

|Old state|New state|  
|---------------|---------------|  
|CONFIRM|RECEIVE|  
|CONFIRM_SEND|SEND|  
|CONFIRM_DEALLOCATE|RESET|  

## Confirmation Requests  
 A confirmation request is issued by one of the following verbs in the partner TP:  

- [MC_CONFIRM](../core/mc-confirm2.md)  

- [MC_PREPARE_TO_RECEIVE](../core/mc-prepare-to-receive1.md) if **ptr_type** is set to AP_SYNC_LEVEL and the conversation's synchronization level (established by [MC_ALLOCATE](../core/mc-allocate2.md)) is AP_CONFIRM_SYNC_LEVEL  

- [MC_DEALLOCATE](../core/mc-deallocate2.md) if **dealloc_type** is set to AP_SYNC_LEVEL and the conversation's synchronization level (established by MC_ALLOCATE) is AP_CONFIRM_SYNC_LEVEL  

- [MC_SEND_DATA](../core/mc-send-data1.md) if type is set to AP_SEND_DATA_CONFIRM and the conversation's synchronization level (established by MC_ALLOCATE) is AP_CONFIRM_SYNC_LEVEL  

  A confirmation request is received by the local TP through the **what_rcvd** parameter of one of the following verbs:  

- [MC_RECEIVE_IMMEDIATE](../core/mc-receive-immediate2.md)  

- [MC_RECEIVE_AND_WAIT](../core/mc-receive-and-wait2.md)  

- [MC_RECEIVE_AND_POST](../core/mc-receive-and-post2.md)  

  **MC_CONFIRMED** is issued by the local TP only if **what_rcvd** contains one of the following values:  

- AP_CONFIRM_WHAT_RECEIVED  

- AP_CONFIRM_SEND  

- AP_CONFIRM_DEALLOCATE  

  If the **rtn_status** parameter is set to AP_YES, **what_rcvd** can also contain the following values:  

- AP_DATA_COMPLETE_CONFIRM  

- AP_DATA_COMPLETE_CONFIRM_SEND  

- AP_DATA_COMPLETE_CONFIRM_DEALL
