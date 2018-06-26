---
title: "TP_STARTED2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4d3155ad-68a0-467d-8141-9f88555e3671
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# TP_STARTED
The **TP_STARTED** verb is issued by the invoking transaction program (TP), and notifies APPC that the TP is starting.  
  
 For the Microsoft® Windows® version 3.*x* system, it is recommended that you use the [WinAsyncAPPC](../core/winasyncappc1.md) function rather than the blocking version of this call.  
  
 The following structure describes the verb control block used by the **TP_STARTED** verb.  
  
## Syntax  
  
```  
  
struct tp_started {  
    unsigned short  opcode;  
    unsigned char   opext;  
    unsigned char   reserv2;  
    unsigned short  primary_rc;  
    unsigned long   secondary_rc;  
    unsigned char   lu_alias[8];  
    unsigned char   tp_id[8];  
    unsigned char   tp_name[64];  
    unsigned char   syncpoint_rqd;  
};   
```  
  
## Remarks  
  
## Members  
 *opcode*  
 Supplied parameter. Specifies the verb operation code, AP_TP_STARTED.  
  
 *opext*  
 Supplied parameter. Specifies the verb operation extension. If the AP_EXTD_VCB bit is set, this indicates that the **tp_started** structure includes the **syncpoint_rqd** member used for Sync Point support. Otherwise, the verb control block ends immediately after the **tp_name** member.  
  
 *reserv2*  
 A reserved field.  
  
 *primary_rc*  
 Returned parameter. Specifies the primary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 *secondary_rc*  
 Returned parameter. Specifies the secondary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 *lu_alias*  
 Supplied parameter. Specifies the alias by which the local LU is known to the local TP.  
  
 The name must match an LU alias established during configuration. APPC checks the LU alias against the current Host Integration Server configuration file. Due to the client/server architecture used by Host Integration Server, however, this parameter is not validated until an [ALLOCATE](../core/allocate2.md) or [MC_ALLOCATE](../core/mc-allocate2.md) is performed.  
  
 This parameter is an 8-byte ASCII character string. It can consist of the following ASCII characters:  
  
- Uppercase letters  
  
- Numerals from 0 through 9  
  
- Spaces  
  
- Special characters $, #, % and @  
  
  The first character of this string cannot be a space.  
  
  If the value of this parameter is fewer than eight bytes in length, pad it on the right with ASCII spaces (0x20).  
  
  To use an LU from the default LU pool, set this field to eight hexadecimal zeros. For more information, see [Default LUs](../core/default-lus2.md).  
  
  *tp_id*  
  Returned parameter. Identifies the newly established TP.  
  
  *tp_name*  
  Supplied parameter. Specifies the name of the local TP.  
  
  Under the Host Integration Server implementation of APPC, this parameter is ignored when issued by **TP_STARTED**. However, this parameter is required if the program runs under the IBM ES for OS/2 version 1.0 implementation of APPC.  
  
  This parameter is a 64-byte EBCDIC character string and is case-sensitive. The **tp_name** parameter can consist of the following EDCDIC characters:  
  
- Uppercase and lowercase letters  
  
- Numerals from 0 through 9  
  
- Special characters $, #, @, and period (.)  
  
  If the TP name is fewer than 64 bytes in length, use EBCDIC spaces (0x40) to pad it on the right.  
  
  The SNA convention for a service TP name is up to four characters. The first character is a hexadecimal byte between 0x00 and 0x3F.  
  
  *syncpoint_rqd*  
  This optional parameter is only applicable if the AP_EXTD_VCB bit is set in the **opext** parameter and Sync Point services are required.  
  
- AP_YES if Sync Point is required.  
  
- AP_NO if Sync Point is not required.  
  
## Return Codes  
 AP_OK  
 Primary return code; the verb executed successfully.  
  
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
  Primary return code; the local TP has issued a call to APPC while APPC was processing another call for the same TP.  
  
  AP_THREAD_BLOCKING  
  Primary return code; the calling thread is already in a blocking call.  
  
  AP_UNEXPECTED_DOS_ERROR  
  Primary return code; the operating system has returned an error to APPC while processing an APPC call from the local TP. The operating system return code is returned through the **secondary_rc**. It appears in Intel byte-swapped order. If the problem persists, consult the system administrator.  
  
## Remarks  
 In response to **TP_STARTED**, APPC generates a TP identifier for the invoking TP. This identifier is a required parameter for subsequent APPC verbs issued by the invoking TP.  
  
 This must be the first APPC verb issued by the invoking TP. Consequently, no prior APPC state exists.  
  
 If the verb executes successfully (**primary_rc** is AP_OK), the state changes to RESET.  
  
## In This Section  
  
-   [Default LUs](../core/default-lus2.md)