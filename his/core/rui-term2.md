---
title: "RUI_TERM2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4a96b2fd-b70d-4b5c-8b95-9c477f002657
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# RUI_TERM
The **RUI_TERM** verb ends both the logical unit (LU) session and the system services control point (SSCP) session for a given LUA LU.  
  
 The following structure describes the **LUA_COMMON** member of the verb control block (VCB) used by **RUI_TERM**.  
  
## Syntax  
  
```  
  
struct LUA_COMMON {  
    unsigned short lua_verb;  
    unsigned short lua_verb_length;  
    unsigned short lua_prim_rc;  
    unsigned long  lua_sec_rc;  
    unsigned short lua_opcode;  
    unsigned long  lua_correlator;  
    unsigned char  lua_luname[8];  
    unsigned short lua_extension_list_offset;  
    unsigned short lua_cobol_offset;  
    unsigned long  lua_sid;  
    unsigned short lua_max_length;  
    unsigned short lua_data_length;  
    char FAR *     lua_data_ptr;  
    unsigned long  lua_post_handle;  
    struct LUA_TH  lua_th;  
    struct LUA_RH  lua_rh;  
    struct LUA_FLAG1 lua_flag1;  
    unsigned char  lua_message_type;  
    struct LUA_FLAG2 lua_flag2;   
    unsigned char  lua_resv56[7];  
    unsigned char  lua_encr_decr_option;  
};  
```  
  
## Members  
 *lua_verb*  
 Supplied parameter. Contains the verb code, LUA_VERB_RUI for Request Unit Interface (RUI) verbs.  
  
 *lua_verb_length*  
 Supplied parameter. Specifies the length in bytes of the logical unit application (LUA) VCB. It must contain the length of the verb record being issued.  
  
 *lua_prim_rc*  
 Primary return code set by LUA at the completion of the verb. The valid return codes vary depending on the LUA verb issued.  
  
 *lua_sec_rc*  
 Secondary return code set by LUA at the completion of the verb. The valid return codes vary depending on the LUA verb issued.  
  
 *lua_opcode*  
 Supplied parameter. Contains the LUA command code (verb operation code) for the verb to be issued, LUA_OPCODE_RUI_TERM.  
  
 *lua_correlator*  
 Supplied parameter. Contains a user-supplied value that links the verb with other user-supplied information. LUA does not use or change this information. This parameter is optional.  
  
 *lua_luname*  
 Supplied parameter. Specifies the ASCII name of the local LU used by the Windows LUA session.  
  
 **RUI_TERM** only requires this parameter if **lua_sid** is zero.  
  
 This parameter is eight bytes long, padded on the right with spaces (0x20) if the name is shorter than eight characters.  
  
 *lua_extension_list_offset*  
 Not used by RUI in Microsoft® Host Integration Server and should be set to zero.  
  
 *lua_cobol_offset*  
 Not used by LUA in Host Integration Server and should be set to zero.  
  
 *lua_sid*  
 Supplied and returned parameter. Specifies the session identifier and is returned by [SLI_OPEN](../core/sli-open2.md) and [RUI_INIT](../core/rui-init1.md). Other verbs use this parameter to identify the session used for the command. If other verbs use the **lua_luname** parameter to identify sessions, set the **lua_sid** parameter to zero.  
  
 *lua_max_length*  
 Not used by **RUI_TERM** and should be set to zero.  
  
 *lua_data_length*  
 Not used by **RUI_TERM** and should be set to zero.  
  
 *lua_data_ptr*  
 Not used by **RUI_TERM** and should be set to zero.  
  
 *lua_post_handle*  
 Supplied parameter. Used under Microsoft Windows Server if asynchronous notification is to be accomplished by events. This variable contains the handle of the event to be signaled or a window handle.  
  
 *lua_th*  
 Not used by **RUI_TERM** and should be set to zero.  
  
 *lua_rh*  
 Not used by **RUI_TERM** and should be set to zero.  
  
 *lua_flag1*  
 Not used by **RUI_TERM** and should be set to zero.  
  
 *lua_message_type*  
 Not used by **RUI_TERM** and should be set to zero.  
  
 *lua_flag2*  
 Not used by **RUI_TERM** and should be set to zero.  
  
 *lua_resv56*  
 Reserved and should be set to zero.  
  
 *lua_encr_decr_option*  
 Reserved and should be set to zero.  
  
## Return Codes  
 *LUA_OK*  
 Primary return code; the verb executed successfully.  
  
 *LUA_PARAMETER_CHECK*  
 Primary return code; the verb did not execute because of a parameter error.  
  
 LUA_BAD_SESSION_ID  
  
 Secondary return code; an invalid value for **lua_sid** was specified in the VCB.  
  
 LUA_INVALID_POST_HANDLE  
  
 Secondary return code; for a Windows operating system using events as the asynchronous posting method, the Windows LUA VCB does not contain a valid event handle.  
  
 LUA_RESERVED_FIELD_NOT_ZERO  
  
 Secondary return code; a reserved field in the verb record or a parameter not used by this verb was set to a nonzero value.  
  
 LUA_VERB_LENGTH_INVALID  
  
 Secondary return code; an LUA verb was issued with the value of **lua_verb_length** unexpected by LUA.  
  
 LUA_STATE_CHECK  
 Primary return code; the verb did not execute because it was issued in an invalid state.  
  
 LUA_NO_RUI_SESSION  
  
 Secondary return code; [RUI_INIT](../core/rui-init1.md) has not yet completed successfully for the LU name specified on **RUI_TERM**.  
  
 LUA_UNSUCCESSFUL  
 Primary return code; the verb record supplied was valid, but the verb did not complete successfully.  
  
 LUA_COMMAND_COUNT_ERROR  
  
 Secondary return code; **RUI_TERM** was already pending when the verb was issued.  
  
 LUA_INVALID_PROCESS  
  
 Secondary return code; the OS/2 process that issued this verb was not the same process that issued **RUI_INIT** for this session. Only the process that started a session can issue verbs on that session.  
  
 LUA_COMM_SUBSYSTEM_ABENDED  
 Primary return code; indicates one of the following conditions:  
  
- The node used by this conversation encountered an ABEND.  
  
- The connection between the transaction program (TP) and the physical unit (PU) 2.1 node was broken (a LAN error).  
  
- The SnaBase at the TPs computer encountered an ABEND.  
  
  LUA_SESSION_FAILURE  
  Primary return code; a required Host Integration Server component has terminated.  
  
  LUA_LU_COMPONENT_DISCONNECTED  
  
  Secondary return code; indicates that the LUA session failed because of a problem with the link service or with the host LU.  
  
  LUA_RUI_LOGIC_ERROR  
  
  Secondary return code; an internal error was detected within LUA. This error should not occur during normal operation.  
  
  LUA_INVALID_VERB  
  Primary return code; either the verb code or the operation code, or both, is invalid. The verb did not execute.  
  
  LUA_STACK_TOO_SMALL  
  Primary return code; the stack size of the application is too small to execute the verb. Increase the stack size of your application.  
  
  LUA_COMM_SUBSYSTEM_NOT_LOADED  
  Primary return code; a required component could not be loaded or has terminated while processing the verb. Thus, communication could not take place. Contact the system administrator for corrective action.  
  
  LUA_UNEXPECTED_DOS_ERROR  
  Primary return code; after issuing an operating system call, an unexpected operating system return code was received and is specified in the secondary return code.  
  
## Remarks  
 This verb can be issued at any time after [RUI_INIT](../core/rui-init1.md) has been issued (whether or not it has completed). If any other LUA verb is pending when **RUI_TERM** is issued, no further processing on the pending verb takes place, and it returns with a primary return code of LUA_CANCELED.  
  
 After this verb has completed, no other LUA verb can be issued for this session.  
  
## See Also  
 [RUI_INIT](../core/rui-init1.md)   
 [SLI_OPEN](../core/sli-open2.md)