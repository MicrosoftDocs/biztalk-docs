---
title: "SLI_CLOSE1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 91e85dfe-c240-4103-a47c-3b3326e3c300
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# SLI_CLOSE
The **SLI_CLOSE** verb ends a session opened with [SLI_OPEN](../core/sli-open2.md). The LU-LU and LU-SSCP resources are released.  
  
 The following structure describes the LUA_COMMON member of the verb control block (VCB) used by SLI_CLOSE.  
  
## Syntax  
  
```  
  
struct LUA_COMMON {  
    unsigned short   lua_verb;  
    unsigned short   lua_verb_length;  
    unsigned short   lua_prim_rc;  
    unsigned long    lua_sec_rc;  
    unsigned short   lua_opcode;  
    unsigned long    lua_correlator;  
    unsigned char    lua_luname[8];  
    unsigned short   lua_extension_list_offset;  
    unsigned short   lua_cobol_offset;  
    unsigned long    lua_sid;  
    unsigned short   lua_max_length;  
    unsigned short   lua_data_length;  
    char FAR *       lua_data_ptr;  
    unsigned long    lua_post_handle;  
    struct LUA_TH    lua_th;  
    struct LUA_RH    lua_rh;  
    struct LUA_FLAG1 lua_flag1;  
    unsigned char    lua_message_type;  
    struct LUA_FLAG2 lua_flag2;  
    unsigned char    lua_resv56[7];  
    unsigned char    lua_encr_decr_option;  
  
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
 Supplied parameter. Contains the LUA command code (verb operation code) for the verb to be issued, LUA_OPCODE_SLI_CLOSE.  
  
 **lua_correlator**  
 Supplied parameter. Contains a user-supplied value that links the verb with other user-supplied information. LUA does not use or change this information. This parameter is optional.  
  
 **lua_luname**  
 Supplied parameter. Specifies the ASCII name of the local LU used by the Windows LUA session.  
  
 SLI_CLOSE only requires this parameter if lua_sid is zero.  
  
 This parameter is eight bytes long, padded on the right with spaces (0x20) if the name is shorter than eight characters.  
  
 **lua_extension_list_offset**  
 Not used by **SLI_CLOSE** and should be set to zero.  
  
 **lua_cobol_offset**  
 Not used by LUA in Microsoft® Host Integration Server  and should be zero.  
  
 **lua_sid**  
 Supplied parameter. Specifies the session identifier and is returned by [SLI_OPEN](../core/sli-open2.md) and [RUI_INIT](../core/rui-init1.md). Other verbs use this parameter to identify the session used for the command. If other verbs use the **lua_luname** parameter to identify sessions, set the **lua_sid** parameter to zero.  
  
 **lua_max_length**  
 Not used by **SLI_CLOSE** and should be set to zero.  
  
 **lua_data_length**  
 Not used by **SLI_CLOSE** and should be set to zero.  
  
 **lua_data_ptr**  
 Not used by **SLI_CLOSE** and should be set to zero.  
  
 **lua_post_handle**  
 Supplied parameter. Used under Microsoft Windows Server if asynchronous notification is to be accomplished by events. This variable contains the handle of the event to be signaled or a window handle.  
  
 **lua_th**  
 Not used by **SLI_CLOSE** and should be set to zero.  
  
 **lua_rh**  
 Not used by **SLI_CLOSE** and should be set to zero.  
  
 **lua_flag1**  
 Supplied parameter. Contains a data structure containing flags for messages supplied by the application. Its subparameters are as follows:  
  
 lua_flag1.bid_enable  
  
 Bid enable indicator, one bit.  
  
 lua_flag1.close_abend  
  
 Close immediate indicator, one bit. A supplied parameter used by **SLI_CLOSE** to specify whether the session is to be closed immediately (ON) or closed normally (OFF). For verbs other than **SLI_CLOSE**, this flag must be off.  
  
 lua_flag1.nowait  
  
 No wait for data flag, one bit.  
  
 lua_flag1.sscp_exp  
  
 System services control point (SSCP) expedited flow, one bit.  
  
 lua_flag1.sscp_norm  
  
 SSCP normal flow, one bit.  
  
 lua_flag1.lu_exp  
  
 LU expedited flow, one bit.  
  
 lua_flag1.lu_norm  
  
 LU normal flow, one bit.  
  
 **lua_message_type**  
 Not used by **SLI_CLOSE** and should be set to zero.  
  
 **lua_flag2**  
 Returned parameter. Contains flags for messages returned by LUA.  
  
 lua_flag2.async  
  
 Indicates that the LUA interface verb completed asynchronously if set to 1.  
  
 **lua_resv56**  
 Reserved and should be set to zero.  
  
 **lua_encr_decr_option**  
 Not used by **SLI_CLOSE** and should be set to zero.  
  
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
  
 LUA_RESERVED_FIELD_NOT_ZERO  
  
 Secondary return code; a reserved parameter for the verb just issued is not set to zero.  
  
 LUA_INVALID_POST_HANDLE  
  
 Secondary return code; for a Microsoft Windows operating system using events as the asynchronous posting method, the Windows LUA VCB does not contain a valid event handle.  
  
 LUA_VERB_LENGTH_INVALID  
  
 Secondary return code; an LUA verb was issued with a value for **lua_verb_length** unexpected by LUA.  
  
 LUA_STATE_CHECK  
 Primary return code; the verb did not execute because it was issued in an invalid state.  
  
 LUA_NO_SLI_SESSION  
  
 Secondary return code; a session was not open or was down due to an **SLI_CLOSE** or session failure when a command was issued.  
  
 LUA_CLOSE_PENDING  
  
 Secondary return code; one of the following has occurred:  
  
- A CLOSE_ABEND was still pending when another CLOSE_ABEND was issued. You can issue a CLOSE_ABEND if a CLOSE_NORMAL is pending.  
  
- Either a CLOSE_ABEND or a CLOSE_NORMAL was still pending when a CLOSE_NORMAL was issued.  
  
  LUA_SESSION_FAILURE  
  Primary return code; an error condition, specified in the secondary return code, caused the session to fail.  
  
  LUA_NOT_ACTIVE  
  
  Secondary return code; LUA was not active within Microsoft Host Integration Server  when an LUA verb was issued.  
  
  LUA_UNEXPECTED_SNA_SEQUENCE  
  
  Secondary return code; unexpected data or commands were received from the host while [SLI_OPEN](../core/sli-open2.md) was processing.  
  
  LUA_NEGATIVE_RSP_CHASE  
  
  Secondary return code; a negative response to an SNA CHASE command from the host was received by the LUA interface while **SLI_CLOSE** was being processed. **SLI_CLOSE** continued processing to stop the session.  
  
  LUA_NEGATIVE_RSP_SHUTC  
  
  Secondary return code; a negative response to an SNA SHUTC command from the host was received by the SLI while **SLI_CLOSE** was still being processed. **SLI_CLOSE** continued processing to stop the session.  
  
  LUA_NEGATIVE_RSP_SHUTD  
  
  Secondary return code; a negative response to an SNA RSHUTD command from the host was received by the LUA interface while **SLI_CLOSE** was still being processed. **SLI_CLOSE** continued processing to stop the session.  
  
  LUA_RECEIVED_UNBIND  
  
  Secondary return code; the primary logical unit (PLU) sent an SNA UNBIND command to the LUA interface when a session was active. As a result, the session was stopped.  
  
  LUA_NO_RUI_SESSION  
  
  Secondary return code; no session has been initialized for the LUA verb issued, or some verb other than [SLI_OPEN](../core/sli-open2.md) was issued before the session was initialized.  
  
  LUA_LU_COMPONENT_DISCONNECTED  
  
  Secondary return code; an LU component is unavailable because it is not connected properly. Make sure that the power is on.  
  
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
 There are two types of **SLI_CLOSE**: normal and ABEND. For a normal close, **lua_flag1.close_abend** is set to zero. The sequence for a normal close can be initiated either as primary (host-initiated) or secondary (requested by a Windows LUA application). During a primary normal close, the Windows LUA interface:  
  
- Reads the SHUTD command and posts the SESSION_END_REQUESTED status to the application.  
  
- Writes the CHASE command (if necessary).  
  
- Reads and processes the CHASE command response (if necessary).  
  
- Writes the shutdown complete (SHUTC) command.  
  
- Reads and processes the SHUTC command response.  
  
- Reads and processes the CLEAR command (if necessary).  
  
- Writes the CLEAR command response (if necessary).  
  
- Reads and processes the UNBIND command.  
  
- Writes the UNBIND command response.  
  
- Stops the session.  
  
  During a secondary normal close, the Windows LUA interface:  
  
- Writes the RSHUTD command.  
  
- Reads and processes the RSHUTD command response.  
  
- Reads and processes the CLEAR command (if necessary).  
  
- Writes the CLEAR command response (if necessary).  
  
- Reads and processes the UNBIND command.  
  
- Writes the UNBIND command response.  
  
- Stops the session.  
  
  For an ABEND close, **lua_flag1.close_abend** is set to 1, which directs the Windows LUA interface to close the session immediately. After **SLI_CLOSE** starts processing, the LU-LU connection is terminated and the SSCP is informed that the LU is not capable of sustaining a session.  
  
## See Also  
 [SLI_OPEN](../core/sli-open2.md)