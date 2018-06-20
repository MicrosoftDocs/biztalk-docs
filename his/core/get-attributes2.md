---
title: "GET_ATTRIBUTES2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3583176c-2b6f-436f-ab53-231826b4eba3
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# GET_ATTRIBUTES
The **GET_ATTRIBUTES** verb returns the attributes of the conversation.  
  
 The following structure describes the verb control block (VCB) used by the **GET_ATTRIBUTES** verb.  
  
## Syntax  
  
```  
  
struct get_attributes {  
    unsigned short   opcode;  
    unsigned char    opext;  
    unsigned char    reserv2;  
    unsigned short   primary_rc;  
    unsigned long    secondary_rc;  
    unsigned char    tp_id[8];  
    unsigned long    conv_id;  
    unsigned char    reserv3;  
    unsigned char    sync_level;  
    unsigned char    mode_name[8];  
    unsigned char    net_name[8];  
    unsigned char    lu_name[8];  
    unsigned char    lu_alias[8];  
    unsigned char    plu_alias[8];  
    unsigned char    plu_un_name[8];  
    unsigned char    reserv4[2];  
    unsigned char    fqplu_name[17];  
    unsigned char    reserv5;  
    unsigned char    user_id[10];  
    unsigned long    conv_group_id;  
    unsigned char    conv_corr_len;  
    unsigned char    conv_corr[8];  
    unsigned char    reserv6[13];  
NOTE: The following fields are present when the high bit of opext is set (opext & AP_EXTD_VCB) != 0.   
    unsigned char    luw_id[26];  
    unsigned char    sess_id[8];  
};   
```  
  
## Members  
 *opcode*  
 Supplied parameter. Specifies the verb operation code, AP_B_GET_ATTRIBUTES.  
  
 *opext*  
 Supplied parameter. Specifies the verb operation extension, AP_BASIC_CONVERSATION.  
  
 *reserv2*  
 A reserved field.  
  
 *primary_rc*  
 Returned parameter. Specifies the primary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 *secondary_rc*  
 Returned parameter. Specifies the secondary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 *tp_id*  
 Supplied parameter. Identifies the local transaction program (TP). The value of this parameter is returned by [TP_STARTED](../core/tp-started2.md) in the invoking TP or by [RECEIVE_ALLOCATE](../core/receive-allocate1.md) in the invoked TP.  
  
 *conv_id*  
 Supplied parameter. Provides the conversation identifier. The value of this parameter is returned by [ALLOCATE](../core/allocate2.md) in the invoking TP or by **RECEIVE_ALLOCATE** in the invoked TP.  
  
 *sync_level*  
 Returned parameter. Specifies the level of synchronization processing for the conversation. This parameter determines whether the TPs can request confirmation of receipt of data and confirm receipt of data.  
  
- AP_NONE indicates that confirmation processing will not be used in this conversation.  
  
- AP_CONFIRM_SYNC_LEVEL indicates that TPs can use confirmation processing in this conversation.  
  
- AP_SYNCPT indicates that TPs can use Sync Point Level 2 confirmation processing in this conversation.  
  
  *mode_name*  
  Returned parameter. Specifies the name of a set of networking characteristics. It is a type A EBCDIC character string.  
  
  *net_name*  
  Returned parameter. Specifies the name of the SNA network containing the local logical unit (LU) used by this TP. It is a type A EBCDIC character string.  
  
  *lu_name*  
  Returned parameter. Provides the name of the local LU.  
  
  *lu_alias*  
  Returned parameter. Provides the alias by which the local LU is known to the local TP. It is an ASCII character string.  
  
  *plu_alias*  
  Returned parameter. Provides the alias by which the partner LU is known to the local TP. It is an ASCII character string.  
  
  *plu_un_name*  
  Returned parameter. Specifies the uninterpreted name of the partner LU—the name of the partner LU as defined to the system services control point (SSCP). It is a type AE EBCDIC character string. This parameter is returned only if the local LU is dependent.  
  
  *fqplu_name*  
  Returned parameter. Provides the fully qualified name of the partner LU. It is a type A EBCDIC character string. The field contains the network name, an EBCDIC period, and the partner-LU name.  
  
  *user_id*  
  Returned parameter. Specifies the user identifier sent by the invoking TP through [ALLOCATE](../core/allocate2.md) to access the invoked TP (if applicable). It is a type AE EBCDIC character string. The field contains the user identifier if the following conditions are true:  
  
- The invoked TP requires conversation security.  
  
- **GET_ATTRIBUTES** was issued by the invoked TP.  
  
  Otherwise, the field contains spaces.  
  
  *conv_group_id*  
  Returned parameter. Specifies the conversation group identifier for the session to which the conversation has been allocated. This is also returned on [ALLOCATE](../core/allocate2.md) and [RECEIVE_ALLOCATE](../core/receive-allocate1.md).  
  
  *conv_corr_len*  
  Returned parameter. Specifies the length of the conversation correlator identifier that is returned.  
  
  *conv_corr*  
  Returned parameter. Specifies the conversation correlator identifier (if any) that the source LU assigns to identify the conversation, which is unique for the source/partner LU pair. It is sent by the source LU on the allocation request.  
  
> [!NOTE]
>  The following fields are present when the high bit of **opext** is set(**opext** & AP_EXTD_VCB) != 0.These fields are only present when using Sync Point Level 2 support.  
  
 *luw_id*  
 Logical unit-of-work identifier.  
  
 *sess_id*  
 Session identifier.  
  
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
  
- The node used by this conversation encountered an ABEND.  
  
- The connection between the TP and the PU 2.1 node has been broken (a LAN error).  
  
- The SnaBase at the TP's computer encountered an ABEND.  
  
  The system administrator should examine the error log to determine the reason for the ABEND.  
  
  AP_CONVERSATION_TYPE_MIXED  
  Primary return code; the TP has issued both basic and mapped conversation verbs. Only one type can be issued in a single conversation.  
  
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