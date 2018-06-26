---
title: "SLI_PURGE1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aa7e551c-572e-4c1e-852b-ca28a0ac27c0
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# SLI_PURGE
The **SLI_PURGE** verb cancels [SLI_RECEIVE](../core/sli-receive2.md) verbs issued with a wait condition.  
  
 The following structure describes the LUA_COMMON member of the verb control block (VCB) used by SLI_PURGE.  
  
## Syntax  
  
```  
  
struct LUA_COMMON {  
    unsigned short    lua_verb;  
    unsigned short    lua_verb_length;  
    unsigned short    lua_prim_rc;  
    unsigned long     lua_sec_rc;  
    unsigned short    lua_opcode;  
    unsigned long     lua_correlator;  
    unsigned char     lua_luname[8];  
    unsigned short    lua_extension_list_offset;  
    unsigned short    lua_cobol_offset;  
    unsigned long     lua_sid;  
    unsigned short    lua_max_length;  
    unsigned short    lua_data_length;  
    char FAR *        lua_data_ptr;  
    unsigned long     lua_post_handle;  
    struct LUA_TH     lua_th;  
    struct LUA_RH     lua_rh;  
    struct LUA_FLAG1  lua_flag1;  
    unsigned char     lua_message_type;  
    struct LUA_FLAG2  lua_flag2;  
    unsigned char     lua_resv56[7];  
    unsigned char     lua_encr_decr_option;  
};  
```  
  
## Members  
 **lua_verb**  
 Supplied parameter. Contains the verb code, LUA_VERB_SLI for Session Level Interface (SLI) verbs.  
  
 **lua_verb_length**  
 Supplied parameter. Specifies the length in bytes of the logical unit application (LUA) VCB. It must contain the length of the verb record being issued.  
  
 **lua_prim_rc**  
 Primary return code set by LUA at the completion of the verb. The valid return codes vary depending on the LUA verb issued.  
  
 **lua_sec_rc**  
 Secondary return code set by LUA at the completion of the verb. The valid return codes vary depending on the LUA verb issued.  
  
 **lua_opcode**  
 Supplied parameter. Contains the LUA command code (verb operation code) for the verb to be issued, LUA_OPCODE_SLI_PURGE.  
  
 **lua_correlator**  
 Supplied parameter. Contains a user-supplied value that links the verb with other user-supplied information. LUA does not use or change this information. This parameter is optional.  
  
 **lua_luname**  
 Supplied parameter. Specifies the ASCII name of the local LU used by the Windows LUA session.  
  
 SLI_PURGE only requires this parameter if lua_sid is zero.  
  
 This parameter is eight bytes long, padded on the right with spaces (0x20) if the name is shorter than eight characters.  
  
 **lua_extension_list_offset**  
 Not used by **SLI_PURGE** and should be set to zero.  
  
 **lua_cobol_offset**  
 Not used by LUA in Microsoft® Host Integration Server or SNA Server and should be zero.  
  
 **lua_sid**  
 Supplied parameter. Specifies the session identifier and is returned by [SLI_OPEN](../core/sli-open2.md) and [RUI_INIT](../core/rui-init1.md). Other verbs use this parameter to identify the session used for the command. If other verbs use the **lua_luname** parameter to identify sessions, set the **lua_sid** parameter to zero.  
  
 **lua_max_length**  
 Not used by **SLI_PURGE** and should be set to zero.  
  
 **lua_data_length**  
 Not used by **SLI_PURGE** and should be set to zero.  
  
 **lua_data_ptr**  
 When **SLI_PURGE** is issued, this parameter points to the location of the [SLI_RECEIVE](../core/sli-receive2.md) verbs VCB that is to be canceled.  
  
 **lua_post_handle**  
 Supplied parameter. Used under Microsoft Windows Server if asynchronous notification is to be accomplished by events. This variable contains the handle of the event to be signaled or a window handle.  
  
 **lua_th**  
 Not used by **SLI_PURGE** and should be set to zero.  
  
 **lua_rh**  
 Not used by **SLI_PURGE** and should be set to zero.  
  
 **lua_flag1**  
 Not used by **SLI_PURGE** and should be set to zero.  
  
 **lua_message_type**  
 Not used by **SLI_PURGE** and should be set to zero.  
  
 **lua_flag2**  
 Returned parameter. Contains flags for messages returned by LUA.  
  
 lua_flag2.async  
  
 Indicates that the LUA interface verb completed asynchronously if set to 1.  
  
 **lua_resv56**  
 Reserved and should be set to zero.  
  
 **lua_encr_decr_option**  
 Not used by **SLI_PURGE** and should be set to zero.  
  
## Return Codes  
 LUA_OK  
 Primary return code; the verb executed successfully.  
  
 LUA_SEC_OK  
  
 Secondary return code; no additional information exists for LUA_OK.  
  
 LUA_PARAMETER_CHECK  
 Primary return code; the verb did not execute because of a parameter error.  
  
 LUA_INVALID_LUNAME  
  
 Secondary return code; an invalid **lua_luname** was specified.  
  
 LUA_BAD_SESSION_ID  
  
 Secondary return code; an invalid value for **lua_sid** was specified in the VCB.  
  
 LUA_BAD_DATA_PTR  
  
 Secondary return code; the **lua_data_ptr** parameter either does not contain a valid pointer or does not point to a read/write segment and supplied data is required.  
  
 LUA_RESERVED_FIELD_NOT_ZERO  
  
 Secondary return code; a reserved parameter for the verb just issued is not set to zero.  
  
 LUA_INVALID_POST_HANDLE  
  
 Secondary return code; for the Microsoft Windows operating system using events as the asynchronous posting method, the Windows LUA VCB does not contain a valid event handle.  
  
 LUA_VERB_LENGTH_INVALID  
  
 Secondary return code; an LUA verb was issued with a value for **lua_verb_length** unexpected by LUA.  
  
 LUA_STATE_CHECK  
 Primary return code; the verb did not execute because it was issued in an invalid state.  
  
 LUA_NO_SLI_SESSION  
  
 Secondary return code; a session was not open or was down due to an [SLI_CLOSE](../core/sli-close1.md) or session failure when a command was issued.  
  
 LUA_NO_RECEIVE_TO_PURGE  
  
 Secondary return code; no [SLI_RECEIVE](../core/sli-receive2.md) was outstanding when you issued **SLI_PURGE**. One of two situations caused the problem:  
  
- **SLI_RECEIVE** completed before **SLI_PURGE** finished processing. You can change the application to take care of this problem because it is not an error condition.  
  
- The lua_data_ptr parameter does not correctly point to the SLI_RECEIVE you want to purge.  
  
  LUA_SLI_PURGE_PENDING  
  
  Secondary return code; an **SLI_PURGE** was still active when another **SLI_PURGE** was issued. Only one **SLI_PURGE** can be active at a time.  
  
  LUA_SESSION_FAILURE  
  Primary return code; an error condition, specified in the secondary return code, caused the session to fail.  
  
  LUA_RECEIVED_UNBIND  
  
  Secondary return code; the primary logical unit (PLU) sent an SNA UNBIND command to the LUA interface when a session was active. As a result, the session was stopped.  
  
  LUA_LU_COMPONENT_DISCONNECTED  
  
  Secondary return code; an LU component is unavailable because it is not connected properly. Make sure that the power is on.  
  
  LUA_UNSUCCESSFUL  
  Primary return code; the verb record supplied was valid but the verb did not complete successfully.  
  
  LUA_VERB_RECORD_SPANS_SEGMENTS  
  
  Secondary return code; the LUA VCB length parameter plus the segment offset is beyond the segment end.  
  
  LUA_NOT_ACTIVE  
  
  Secondary return code; LUA was not active within Microsoft Host Integration Server or SNA Server when an LUA verb was issued.  
  
  LUA_NOT_READY  
  
  Secondary return code; one of the following caused the SLI session to be temporarily suspended:  
  
- An SNA UNBIND type 0x02 command was received, which indicates a new BIND is coming. If the UNBIND type 0x02 is received after the beginning [SLI_OPEN](../core/sli-open2.md) is complete, the session is suspended until a BIND, optional CRV and STSN, and SDT flows are received. These routines are re-entrant because they have to be called again. The session resumes after the SLI processes the SDT command. If the UNBIND type 0x02 is received while the **SLI_OPEN** is still processing, the primary return code is SESSION_FAILURE, not LUA_STATUS.  
  
- The receipt of an SNA CLEAR caused the suspension. Receipt of an SNA SDT will cause the session to resume.  
  
  LUA_INVALID_PROCESS  
  
  Secondary return code; the session for which a Request Unit Interface (RUI) verb was issued is unavailable because another OS/2 process owns the session.  
  
  LUA_LU_INOPERATIVE  
  
  Secondary return code; a severe error occurred while the RUI was attempting to stop the session. This LU is unavailable for any LUA requests until an activate logical unit (ACTLU) is received from the host.  
  
  LUA_CANCELED  
  Primary return code; the secondary return code gives the reason for canceling the command.  
  
  LUA_TERMINATED  
  
  Secondary return code; the session was terminated when a verb was pending. The verb process was canceled.  
  
  LUA_IN_PROGRESS  
  Primary return code; an asynchronous command was received but is not completed.  
  
  LUA_COMM_SUBSYSTEM_ABENDED  
  Primary return code; indicates one of the following conditions:  
  
- The node used by this conversation encountered an ABEND.  
  
- The connection between the transaction program (TP) and the physical unit (PU) 2.1 node has been broken (a LAN error).  
  
- The SnaBase at the TPs computer encountered an ABEND.  
  
  LUA_COMM_SUBSYSTEM_NOT_LOADED  
  Primary return code; a required component could not be loaded or terminated while processing the verb. Thus, communication could not take place. Contact the system administrator for corrective action.  
  
  LUA_INVALID_VERB_SEGMENT  
  Primary return code; the VCB extended beyond the end of the data segment.  
  
  LUA_UNEXPECTED_DOS_ERROR  
  Primary return code; after issuing an operating system call, an unexpected operating system return code was received and is specified in the secondary return code.  
  
  LUA_STACK_TOO_SMALL  
  Primary return code; the stack size of the application is too small to execute the verb. Increase the stack size of your application.  
  
  LUA_INVALID_VERB  
  Primary return code; either the verb code or the operation code, or both, is invalid. The verb did not execute.  
  
## Remarks  
 **SLI_PURGE** cancels [SLI_RECEIVE](../core/sli-receive2.md) commands with a wait condition.  
  
 Typically, SLI_PURGE is issued if SLI_RECEIVE takes too long to complete. To cancel an SLI_RECEIVE, lua_data_ptr has to point to the SLI_RECEIVE VCB to cancel. The primary return code of the SLI_RECEIVE will be set to LUA_CANCELED when SLI_PURGE succeeds in canceling SLI_RECEIVE.  
  
## See Also  
 [RUI_INIT](../core/rui-init1.md)   
 [SLI_OPEN](../core/sli-open2.md)   
 [SLI_RECEIVE](../core/sli-receive2.md)   
 [SLI_SEND](../core/sli-send2.md)