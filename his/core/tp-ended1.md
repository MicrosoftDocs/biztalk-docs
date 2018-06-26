---
title: "TP_ENDED1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3f50207d-8bc2-49fd-99bb-57f68e90faa1
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# TP_ENDED
The **TP_ENDED** verb is issued by both the invoking and invoked transaction program (TP), and notifies APPC that the TP is ending.  
  
 For the Microsoft® Windows® version 3.*x* system, it is recommended that you use the [WinAsyncAPPC](../core/winasyncappc1.md) function rather than the blocking version of this call.  
  
 The following structure describes the verb control block (VCB) used by the **TP_ENDED** verb.  
  
## Syntax  
  
```  
  
struct tp_ended {  
    unsigned short  opcode;  
    unsigned char   opext;  
    unsigned char   reserv2;  
    unsigned short  primary_rc;  
    unsigned long   secondary_rc;  
    unsigned char   tp_id[8];  
    unsigned char   type;  
};   
```  
  
## Members  
 *opcode*  
 Supplied parameter. Specifies the verb operation code, AP_TP_ENDED.  
  
 *opext*  
 Supplied parameter. Specifies the verb operation extension. This field is not used by the **TP_ENDED** verb.  
  
 *reserv2*  
 A reserved field.  
  
 *primary_rc*  
 Returned parameter. Specifies the primary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 *secondary_rc*  
 Returned parameter. Specifies the secondary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 *tp_id*  
 Supplied parameter. Identifies the local TP. The value of this parameter was returned by [TP_STARTED](../core/tp-started2.md) in the invoking TP or by [RECEIVE_ALLOCATE](../core/receive-allocate1.md) in the invoked TP.  
  
 *type*  
 Supplied parameter. Specifies the type of termination to be performed. The following are allowed values:  
  
-   AP_HARD indicates that all active verbs for the TP are terminated; the session(s) being used by the conversation(s) are ended. Both the local TP and the partner TP can receive conversation failure return codes (AP_DEALLOC_ABEND for mapped conversations and AP_DEALLOC_ABEND_PROG for basic conversations).  
  
-   AP_SOFT indicates that the TP waits for all active verbs to complete; the session being used by the conversation remains active.  
  
## Return Codes  
 AP_OK  
 Primary return code; the verb executed successfully.  
  
 AP_PARAMETER_CHECK  
 Primary return code; the verb did not execute because of a parameter error.  
  
 AP_BAD_TP_ID  
  
 Secondary return code; APPC did not recognize the **tp_id** as an assigned TP identifier.  
  
 AP_BAD_TYPE  
  
 Secondary return code; the specified **type** value was not recognized by APPC.  
  
 AP_COMM_SUBSYSTEM_ABENDED  
 Primary return code; indicates one of the following conditions:  
  
- The node used by this conversation encountered an ABEND.  
  
- The connection between the TP and the PU 2.1 node has been broken (a LAN error).  
  
- The SnaBase at the TP's computer encountered an ABEND.  
  
  The system administrator should examine the error log to determine the reason for the ABEND.  
  
  AP_COMM_SUBSYSTEM_NOT_LOADED  
  Primary return code; a required component could not be loaded or terminated while processing the verb. Thus, communication could not take place. Contact the system administrator for corrective action.  
  
  AP_INVALID_VERB_SEGMENT  
  Primary return code; the VCB extended beyond the end of the data segment.  
  
  AP_STACK_TOO_SMALL  
  Primary return code; the stack size of the application is too small to execute the verb. Increase the stack size of your application.  
  
  AP_TP_BUSY  
  Primary return code; the local TP has issued a call to APPC while APPC was processing another call for the same TP. This can occur if the local TP has multiple threads, and more than one thread is issuing APPC calls using the same **tp_id**.  
  
  AP_THREAD_BLOCKING  
  Primary return code; the calling thread is already in a blocking call.  
  
  AP_UNEXPECTED_DOS_ERROR  
  Primary return code; the operating system has returned an error to APPC while processing an APPC call from the local TP. The operating system return code is returned through the **secondary_rc**. It appears in Intel byte-swapped order. If the problem persists, consult the system administrator.  
  
## Remarks  
 In response to **TP_ENDED**, APPC frees the resources used by the TP. After this verb executes, the TP identifier is no longer valid; the TP cannot issue any more APPC conversation verbs.  
  
 The conversation can be in any state when the TP issues this verb.  
  
 If the conversation is in SEND state, **TP_ENDED** performs the function of [DEALLOCATE](../core/deallocate2.md) or [MC_DEALLOCATE](../core/mc-deallocate2.md) with **dealloc_type** set to AP_FLUSH.  
  
 If the conversation is in a state other than RESET or SEND, **TP_ENDED** performs the function of **DEALLOCATE** or **MC_DEALLOCATE** with **dealloc_type** set to AP_ABEND (for a mapped conversation) or AP_ABEND_PROG (for a basic conversation).  
  
 After successful execution (**primary_rc** is AP_OK), there is no APPC state.