---
title: "GET_LU_STATUS2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aa453759-b105-4ffb-a1c1-9ee93ededb6d
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# GET_LU_STATUS
The **GET_LU_STATUS** verb returns the status of a particular logical unit (LU). This conversation verb is only available when Sync Point conversations are supported.  
  
 The following structure describes the verb control block (VCB) used by the **GET_LU_STATUS** verb.  
  
## Syntax  
  
```  
  
struct get_type {  
    unsigned short   opcode;  
    unsigned char    opext;  
    unsigned char    reserv2;  
    unsigned short   primary_rc;  
    unsigned long    secondary_rc;  
    unsigned char    tp_id[8];  
    unsigned char    plu_alias[8];  
    unsigned short   active_sess;  
    unsigned char    zero_sess;  
    unsigned char    local_only;  
    unsigned char    synchpoint;  
    unsigned char    pool_member;  
    unsigned char    reserv3[7];  
};   
```  
  
## Members  
 opcode  
 Supplied parameter. Specifies the verb operation code, AP_GET_LU_STATUS.  
  
 opext  
 This field is unused by the **GET_LU_STATUS** verb.  
  
 reserv2  
 A reserved field.  
  
 primary_rc  
 Returned parameter. Specifies the primary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 secondary_rc  
 Returned parameter. Specifies the secondary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 tp_id  
 Supplied parameter. Identifies the local transaction program (TP). The value of this parameter was returned by [TP_STARTED](../core/tp-started2.md) in the invoking TP, or by [RECEIVE_ALLOCATE](../core/receive-allocate1.md) or RECEIVE_ALLOCATE_EX in the invoked TP.  
  
 plu_alias  
 Supplied parameter. Provides the identifier for the LU about which this TP is inquiring. The value of this parameter was returned by [MC_ALLOCATE](../core/mc-allocate2.md) or [ALLOCATE](../core/allocate2.md) in the invoking TP or by **RECEIVE_ALLOCATE** in the invoked TP.  
  
 Not required if local_only is set to AP_YES  
  
 active_sess  
 Returned parameter. Supplies the number of active sessions on this LU.  
  
 zero_sess  
 Returned parameter. Indicates whether a zero session is on this LU. Values are AP_YES or AP_NO.  
  
 active_sess  
 Returned parameter.  
  
 zero_sess  
 Returned parameter.  
  
 local_only  
 If this field is set to AP_YES then the plu_alias does not need to be specified and the verb only returns the local LU information - syncpoint and default_pool.  
  
 synchpoint  
 Returned parameter.  
  
 pool_member  
 If this field is set to AP_YES then the plu_alias does not need to be specified and the verb only returns the local LU information - syncpoint and default_pool.  
  
 *reserv3*  
 A reserved field.  
  
## Return Codes  
 AP_OK  
 Primary return code; the verb executed successfully.  
  
 AP_PARAMETER_CHECK  
 Primary return code; the verb did not execute because of a parameter error.  
  
 AP_BAD_LU_ALIAS  
  
 Secondary return code; the value of **plu_alias** did not match any LUs assigned by APPC.  
  
 AP_BAD_TP_ID  
  
 Secondary return code; the value of **tp_id** did not match a TP identifier assigned by APPC.  
  
 AP_COMM_SUBSYSTEM_ABENDED  
 Primary return code; indicates one of the following conditions:  
  
- The node used by this conversation encountered an ABEND.  
  
- The connection between the TP and the PU 2.1 node has been broken (a LAN error).  
  
- The SnaBase at the TP's computer encountered an ABEND.  
  
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
 The conversation can be in any state except RESET when the TP issues this verb.  
  
 There is no state change.  
  
 The current version of GET_LU_STATUS allows for an application to retrieve configuration parameters for a Local APPC LU.  
  
 To check the configuration of a particular Local LU before issuing a RECEIVE_ALLOCATE_EX verb, the following verb sequence should be issued:  
  
-   TP_STARTED (specifying the Local LU of interest)  
  
-   GET_LU_STATUS (with local_only set to AP_YES)  
  
-   TP_ENDED (AP_SOFT)