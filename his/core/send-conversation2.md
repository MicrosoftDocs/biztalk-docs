---
title: "SEND_CONVERSATION2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 93038595-1cf5-4736-9c75-9bc5f1ab5352
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# SEND_CONVERSATION
The **SEND_CONVERSATION** verb allocates a session between the local logical unit (LU) and partner LU, sends data on the session, and then deallocates the session.  
  
 The following structure describes the verb control block (VCB) used by the **SEND_CONVERSATION** verb.  
  
## Syntax  
  
```  
  
struct send_conversation {  
    unsigned short      opcode;  
    unsigned char       opext;  
    unsigned char       reserv2;  
    unsigned short      primary_rc;  
    unsigned long       secondary_rc;  
    unsigned char       tp_id[8];  
    unsigned long       conv_id;  
       unsigned char       reserv3[8];  
    unsigned char       rtn_ctl;  
    unsigned char       reserv4;  
    unsigned long       conv_group_id;  
    unsigned long       sense_data;  
    unsigned char       plu_alias[8];  
    unsigned char       mode_name[8];  
    unsigned char       tp_name[64];  
    unsigned char       security;  
    unsigned char       reserv6[11];  
    unsigned char       pwd[10];  
    unsigned char       user_id[10];  
    unsigned short      pip_dlen;  
    unsigned char FAR * pip_dptr;  
    unsigned char       reserv6;  
    unsigned char       fqplu_name[17];  
    unsigned char       reserv7[8];  
    unsigned short      dlen;  
    unsigned char FAR * dptr;  
};   
```  
  
## Members  
 *opcode*  
 Supplied parameter. Specifies the verb operation code, AP_B_SEND_CONVERSATION.  
  
 *opext*  
 Supplied parameter. Specifies the verb operation extension, AP_BASIC_CONVERSATION.  
  
 *reserv2*  
 A reserved field.  
  
 *primary_rc*  
 Returned parameter. Specifies the primary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 *secondary_rc*  
 Returned parameter. Specifies the secondary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 *tp_id*  
 Supplied parameter. Identifies the local transaction program (TP). The value of this parameter was returned by [TP_STARTED](../core/tp-started2.md).  
  
 *conv_id*  
 Supplied parameter. Provides the conversation identifier.  
  
 The value of this parameter is returned by [ALLOCATE](../core/allocate2.md) in the invoking TP or by [RECEIVE_ALLOCATE](../core/receive-allocate1.md) in the invoked TP.  
  
 *rtn_ctl*  
 Supplied parameter. Specifies how APPC should select a session to allocate for the conversation and when the local LU should return control to the local TP. The allowed values are:  
  
- AP_IMMEDIATE specifies that the LU allocates a contention-winner session, if one is immediately available, and returns control to the TP.  
  
- AP_WHEN_SESSION_ALLOCATED specifies that the LU does not return control to the TP until it allocates a session or encounters one of the errors described in Return Codes in this topic. If the session limit is zero, the LU returns control immediately. Note that if a session is not available, the TP waits for one.  
  
- AP_WHEN_SESSION_FREE specifies that the LU allocates a contention-winner or contention-loser session, if one is available or able to be activated, and returns control to the TP. If an error occurs (as described in Return Codes in this topic) the call will return immediately with the error in the **primary_rc** and **secondary_rc** fields.  
  
- AP_WHEN_CONWINNER_ALLOC specifies that the LU does not return control until it allocates a contention-winner session or encounters one of the errors described in Return Codes in this topic. If the session limit is zero, the LU returns control immediately. Note that if a session is not available, the TP waits for one.  
  
- AP_WHEN_CONV_GROUP_ALLOC specifies that the LU does not return control to the TP until it allocates the session specified by **conv_group_id** or encounters one of the errors described in Return Codes in this topic. If the session is not available, the TP waits for it to become free.  
  
  *conv_group_id*  
  Supplied/returned parameter. Used as a supplied parameter when **rtn_ctl** is WHEN_CONV_GROUP_ALLOC to specify the identity of the conversation group from which the session should be allocated. When **rtn_ctl** specifies a different value, and the **primary_rc** is AP_OK, this is a returned value. The purpose of this parameter is to provide a TP with the assurance that the same session will be reallocated and therefore the conversations conducted over the session will occur in the same sequence that they were initiated.  
  
  *sense_data*  
  Returned parameter. If the primary and secondary return codes indicate an allocation error (retry or no-retry), an SNA-defined sense code is returned.  
  
  *plu_alias*  
  Supplied parameter. Specifies the alias by which the partner LU is known to the local TP. This parameter must match the name of a partner LU established during configuration. The parameter is an 8-byte, type G ASCII character set that includes:  
  
- Uppercase letters  
  
- Numerals 0 to 9  
  
- Spaces  
  
- Special characters $, #, %, and @  
  
  If the value of this parameter is fewer than eight bytes, pad it on the right with ASCII spaces (0x20).  
  
  *mode_name*  
  Supplied parameter. Specifies the name of a set of networking characteristics defined during configuration. This parameter must match the name of a mode associated with the partner LU during configuration.  
  
  The parameter is an 8-byte EBCDIC character string. It can consist of characters from the type A EBCDIC character set, including all EBCDIC spaces. These characters are:  
  
- Uppercase letters  
  
- Numerals 0 to 9  
  
- Special characters $, #, and @  
  
  The first character in the string must be an uppercase letter or special character.  
  
  Using the name SNASVCMG (a reserved mode name used internally by APPC) in a basic conversation is not recommended.  
  
  *tp_name*  
  Supplied parameter. Specifies the name of the invoked TP. The value of **tp_name** specified by [ALLOCATE](../core/allocate2.md) in the invoking TP must match the value of **tp_name** specified by [RECEIVE_ALLOCATE](../core/receive-allocate1.md) in the invoked TP.  
  
  The parameter is a 64-byte, case-sensitive, EBCDIC character string. This parameter can consist of characters from the type AE EBCDIC character set. These characters are:  
  
- Uppercase and lowercase letters  
  
- Numerals 0 to 9  
  
- Special characters $, #, @, and period (.)  
  
  If the TP name is fewer than 64 bytes, use EBCDIC spaces (0x40) to pad it on the right.  
  
  The SNA convention for naming a service TP is up to four characters. The first character is a hexadecimal byte between 0x00 and 0x3F. The other characters are from the EBCDIC AE character set.  
  
  *security*  
  Supplied parameter. Specifies the information the partner LU requires in order to validate access to the invoked TP.  
  
- AP_NONE specifies that the invoked TP uses no conversation security.  
  
- AP_PGM specifies that the invoked TP uses conversation security and requires a user identifier and password. Use **user_id** and **pwd** to supply this information.  
  
- AP_SAME specifies that the invoked TP, invoked with a valid user identifier and password, in turn invokes another TP.  
  
  For example, assume that TP A invokes TP B with a valid user identifier and password, and TP B in turn invokes TP C. If TP B specifies the value AP_SAME, APPC will send the LU for TP C the user identifier from TP A and an already-verified indicator. This indicator indicates to TP C not to require the password (if TP C is configured to accept an already-verified indicator).  
  
  *pwd*  
  Supplied parameter. Specifies the password associated with **user_id**. This parameter is required only if the security parameter is set to AP_PGM and must match the password for **user_id** that was established during configuration.  
  
  This parameter is a 10-byte, case-sensitive, EBCDIC character string. It can consist of characters from the type AE EBCDIC character set. These characters are:  
  
- Uppercase and lowercase letters  
  
- Numerals 0 to 9  
  
- Special characters $, #, @, and period (.)  
  
  If the password is fewer than 10 bytes, use EBCDIC spaces (0x40) to pad it on the right.  
  
  *user_id*  
  Supplied parameter. Specifies the user identifier required to access the partner TP. This parameter is required only if the security parameter is set to AP_PGM and must match one of the user identifiers configured for the partner TP.  
  
  The parameter can consist of characters from the type AE EBCDIC character set. These characters are:  
  
- Uppercase and lowercase letters  
  
- Numerals 0 to 9  
  
- Special characters $, #, @, and period (.)  
  
  If the user identifier is fewer than 10 bytes, use EBCDIC spaces (0x40) to pad it on the right.  
  
  *pip_dlen*  
  Supplied parameter. Specifies the length of the PIP to be passed to the partner TP. The range for this parameter is from 0 through 32767.  
  
  *pip_dptr*  
  Supplied parameter. Specifies the address of the buffer containing PIP data. Use this parameter only if **pip_dlen** is greater than zero.  
  
  PIP data can consist of initialization parameters or environmental setup information required by a partner TP or remote operating system. The PIP data must follow the GDS format. For more information, see your IBM SNA manual(s).  
  
  For the Microsoft Windows operating system, the data buffer can reside in a static data area or in a globally allocated area.  
  
  *fqplu_name*  
  Supplied parameter. Specifies the fully qualified name of the local LU. This parameter must match the fully qualified name of the local LU defined in the remote node. The parameter is made up of two type A EBCDIC character strings (each of up to eight characters), which are the network name (NETID) and the LU name of the partner LU. The names are separated by an EBCDIC period (.). The NETID can be omitted, and if this is the case, the period should also be omitted.  
  
  This name must be provided if no **plu_alias** is provided.  
  
  Type A EBCDIC characters contain:  
  
- Uppercase letters  
  
- Numerals 0 to 9  
  
- Special characters $, #, and @  
  
  If the value of this parameter is fewer than 17 bytes, pad it on the right with EBCDIC spaces (0x40).  
  
  *dlen*  
  Supplied parameter. Specifies the number of bytes of data to be put in the local LU's send buffer. The range for this parameter is from 0 through 65535.  
  
  *dptr*  
  Supplied parameter. Specifies the address of the buffer containing the data to be put in the local LU's send buffer.  
  
  For the Windows operating system, the data buffer can reside in a static data area or in a globally allocated area. The data buffer must fit entirely within this area.  
  
## Return Codes  
 AP_OK  
 Primary return code; the verb executed successfully.  
  
 AP_UNSUCCESSFUL  
 Primary return code; the supplied parameter **rtn_ctl** specified immediate return of the control to the TP (AP_IMMEDIATE), and the local LU did not have an available contention-winner session.  
  
 AP_PARAMETER_CHECK  
 Primary return code; the verb did not execute because of a parameter error.  
  
 AP_BAD_RETURN_CONTROL  
  
 Secondary return code; the value specified for **rtn_ctl** was invalid.  
  
 AP_BAD_SECURITY  
  
 Secondary return code; the value specified for **security** was invalid.  
  
 AP_BAD_TP_ID  
  
 Secondary return code; the value of **tp_id** did not match a TP identifier assigned by APPC.  
  
 AP_PIP_LEN_INCORRECT  
  
 Secondary return code; the value of **pip_dlen** was greater than 32767.  
  
 AP_UNKNOWN_PARTNER_MODE  
  
 Secondary return code; the value specified for **mode_name** was invalid.  
  
 AP_BAD_PARTNER_LU_ALIAS  
  
 Secondary return code; APPC did not recognize the supplied **partner_lu_alias**.  
  
 AP_ALLOCATION_ERROR  
 Primary return code; APPC has failed to allocate a conversation. The conversation state is set to RESET.  
  
 This code may be returned through a verb issued after [ALLOCATE](../core/allocate2.md).  
  
 AP_ALLOCATION_FAILURE_NO_RETRY  
  
 Secondary return code; the conversation cannot be allocated because of a permanent condition, such as a configuration error or session protocol error. To determine the error, the system administrator should examine the error log file. Do not retry the allocation until the error has been corrected.  
  
 AP_ALLOCATION_FAILURE_RETRY  
  
 Secondary return code; the conversation could not be allocated because of a temporary condition, such as a link failure. The reason for the failure is logged in the system error log. Retry the allocation.  
  
 AP_COMM_SUBSYSTEM_ABENDED  
 Primary return code; indicates one of the following conditions:  
  
- The node used by this conversation encountered an ABEND.  
  
- The connection between the TP and the PU 2.1 node has been broken (a LAN error).  
  
- The SnaBase at the TP's computer encountered an ABEND.  
  
  The system administrator should examine the error log to determine the reason for the ABEND.  
  
  AP_COMM_SUBSYSTEM_NOT_LOADED  
  Primary return code; a required component could not be loaded or has terminated while processing the verb. Thus, communication could not take place. Contact the system administrator for corrective action.  
  
  When this return code is used with [ALLOCATE](../core/allocate2.md), it may indicate that no communications system could be found to support the local LU. (For example, the local LU alias specified with [TP_STARTED](../core/tp-started2.md) is incorrect or has not been configured.) Note that if **lu_alias** or **mode_name** is fewer than eight characters, you must ensure that these fields are filled with spaces to the right. This error is returned if these parameters are not filled with spaces, since there is no node available that can satisfy the **ALLOCATE** request.  
  
  When **ALLOCATE** produces this return code for a Host Integration Server Client system configured with multiple nodes, there are two secondary return codes as follows:  
  
  0xF0000001  
  
  Secondary return code; no nodes have been started.  
  
  0xF0000002  
  
  Secondary return code; at least one node has been started, but the local LU (when **TP_STARTED** is issued) is not configured on any active nodes. The problem could be either of the following:  
  
- The node with the local LU is not started.  
  
- The local LU is not configured.  
  
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
 This verb is issued by the invoking TP to conduct an entire conversation with the remote TP. If the remote TP rejects either the conversation initiation or the data, the invoking TP will not receive notification of the rejection.  
  
 The conversation state is RESET when the TP issues this verb. There is no state change.  
  
 Several parameters of **SEND_CONVERSATION** are EBCDIC or ASCII strings. A TP can use the CSV [CONVERT](../core/convert2.md) to translate a string from one character set to the other.  
  
 Normally, the value of **mode_name** must match the name of a mode configured for the invoked TP's node and associated during configuration with the partner LU. If one of the modes associated with the partner LU on the invoked TP's node is an implicit mode, the session established between the two LUs will be of the implicit mode when no mode name associated with the partner LU matches the value of **mode_name**.