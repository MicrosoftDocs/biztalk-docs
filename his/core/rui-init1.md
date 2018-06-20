---
title: "RUI_INIT1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: df5c593f-e8cc-4b24-a499-24295171d546
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# RUI_INIT
The **RUI_INIT** verb transfers control of the specified logical unit (LU) to the Microsoft® Windows® logical unit application (LUA) application. **RUI_INIT** establishes a session between the system services control point (SSCP) and the specified LU.  
  
> [!NOTE]
>  For 3270 emulator users, a Microsoft Host Integration Server extension has been added that enables you to use 3270 LUs rather than the LUA LUs. For more information, see Remarks in this topic.  
  
 The following structure describes the **LUA_COMMON** member of the verb control block (VCB) used by **RUI_INIT**.  
  
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
 Supplied parameter. Specifies the length in bytes of the LUA VCB. It must contain the length of the verb record being issued.  
  
 *lua_prim_rc*  
 Primary return code set by LUA at the completion of the verb. The valid return codes vary depending on the LUA verb issued.  
  
 *lua_sec_rc*  
 Secondary return code set by LUA at the completion of the verb. The valid return codes vary depending on the LUA verb issued.  
  
 *lua_opcode*  
 Supplied parameter. Contains the LUA command code (verb operation code) for the verb to be issued, LUA_OPCODE_RUI_INIT.  
  
 *lua_correlator*  
 Supplied parameter. Contains a user-supplied value that links the verb with other user-supplied information. LUA does not use or change this information. This parameter is optional.  
  
 *lua_luname*  
 Supplied parameter. Specifies the ASCII name of the local LU used by the Windows LUA session.  
  
 **RUI_INIT** requires this parameter.  
  
 This parameter is eight bytes long, padded on the right with spaces (0x20) if the name is shorter than eight characters.  
  
 *lua_extension_list_offset*  
 Not used by RUI in Host Integration Server and should be set to zero.  
  
 *lua_cobol_offset*  
 Not used by LUA in Host Integration Server and should be zero.  
  
 *lua_sid*  
 Returned parameter. Specifies the session identifier.  
  
 *lua_max_length*  
 Not used by **RUI_INIT** and should be set to zero.  
  
 *lua_data_length*  
 Not used by **RUI_INIT** and should be set to zero.  
  
 *lua_data_ptr*  
 Not used by **RUI_INIT** and should be set to zero.  
  
 *lua_post_handle*  
 Supplied parameter. Used under Microsoft® Windows Server if asynchronous notification is to be accomplished by events. This variable contains the handle of the event to be signaled or a window handle.  
  
 *lua_th*  
 Not used by **RUI_INIT** and should be set to zero.  
  
 *lua_rh*  
 Not used by **RUI_INIT** and should be set to zero.  
  
 *lua_flag1*  
 Not used by **RUI_INIT** and should be set to zero.  
  
 *lua_message_type*  
 Specifies the type of the inbound or outbound SNA commands and data. This is a returned parameter for **RUI_INIT**. Possible values are:  
  
 LUA_MESSAGE_TYPE_LU_DATA  
  
 LUA_MESSAGE_TYPE_SSCP_DATA  
  
 LUA_MESSAGE_TYPE_BID  
  
 LUA_MESSAGE_TYPE_BIND  
  
 LUA_MESSAGE_TYPE_BIS  
  
 LUA_MESSAGE_TYPE_CANCEL  
  
 LUA_MESSAGE_TYPE_CHASE  
  
 LUA_MESSAGE_TYPE_CLEAR  
  
 LUA_MESSAGE_TYPE_CRV  
  
 LUA_MESSAGE_TYPE_LUSTAT_LU  
  
 LUA_MESSAGE_TYPE_LUSTAT_SSCP  
  
 LUA_MESSAGE_TYPE_QC  
  
 LUA_MESSAGE_TYPE_QEC  
  
 LUA_MESSAGE_TYPE_RELQ  
  
 LUA_MESSAGE_TYPE_RQR  
  
 LUA_MESSAGE_TYPE_RTR  
  
 LUA_MESSAGE_TYPE_SBI  
  
 LUA_MESSAGE_TYPE_SHUTD  
  
 LUA_MESSAGE_TYPE_SIGNAL  
  
 LUA_MESSAGE_TYPE_SDT  
  
 LUA_MESSAGE_TYPE_STSN  
  
 LUA_MESSAGE_TYPE_UNBIND  
  
 The Session Level Interface (SLI) receives and responds to the BIND, CRV, and STSN requests through the LUA interface extension routines.  
  
 LU_DATA, LUSTAT_LU, LUSTAT_SSCP, and SSCP_DATA are not SNA commands.  
  
 *lua_flag2*  
 Returned parameter. Contains flags for messages returned by LUA.  
  
 *lua_flag2.async*  
  
 Indicates that the LUA interface verb completed asynchronously if set to 1.  
  
 **RUI_INIT** always completes asynchronously unless it returns an error such as LUA_PARAMETER_CHECK).  
  
 *lua_resv56*  
 Supplied parameter. A reserved field used by **RUI_INIT** and [SLI_OPEN](../core/sli-open2.md). All other reserved fields in the array must be left blank. For more information, see the discussion of these Host Integration Server extensions in the Remarks section.  
  
 lua_resv56[1]  
  
 Supplied parameter. Indicates whether an RUI application can access LUs configured as 3270 LUs, in addition to LUA LUs. If this parameter is nonzero, 3270 LUs can be accessed.  
  
 lua_resv56[2]  
  
 Supplied parameter. Indicates whether the RUI library will release the LU when the LU-SSCP session or connection goes away. If this parameter is nonzero, the LU will not be released.  
  
 lua_resv56[3]  
  
 Supplied parameter. Indicates whether incomplete reads are supported. If this parameter is set to a nonzero value, incomplete or truncated reads are supported. For more details, see the remarks for [RUI_READ](../core/rui-read2.md).  
  
 lua_resv56[4]  
  
 Supplied parameter. Indicates whether the RUI library will allow the application to keep hold of the LU if it is recycled at the host. If this parameter is nonzero, the application can keep hold of the LU.  
  
 *lua_encr_decr_option*  
 Field for cryptography options. On **RUI_INIT**, only the following are supported:  
  
 **lua_encr_decr_option** = 0  
  
 **lua_encr_decr_option** = 128  
  
 Values from 1 through 127 are not supported.  
  
## Return Codes  
 LUA_OK  
 Primary return code; the verb executed successfully.  
  
 LUA_CANCELED  
 Primary return code; the verb did not complete successfully because it was canceled by another verb.  
  
 LUA_TERMINATED  
  
 Secondary return code; [RUI_TERM](../core/rui-term2.md) was issued before **RUI_INIT** completed.  
  
 LUA_PARAMETER_CHECK  
 Primary return code; the verb did not execute because of a parameter error.  
  
 LUA_INVALID_LUNAME  
  
 Secondary return code; the **lua_luname** parameter did not match any LUA LU name or LU pool name in the configuration file.  
  
 LUA_INVALID_POST_HANDLE  
  
 Secondary return code; for a Windows operating system using events as the asynchronous posting method, the Windows LUA VCB does not contain a valid event handle.  
  
 LUA_RESERVED_FIELD_NOT_ZERO  
  
 Secondary return code; a reserved field in the verb record, or a parameter not used by this verb, was set to a nonzero value.  
  
 LUA_VERB_LENGTH_INVALID  
  
 Secondary return code; an LUA verb was issued with the value of **lua_verb_length** unexpected by LUA.  
  
 LUA_STATE_CHECK  
 Primary return code; the verb did not execute because it was issued in an invalid state.  
  
 LUA_DUPLICATE_RUI_INIT  
  
 Secondary return code; the **lua_luname** parameter specified an LU name or LU pool name already in use by this application (or for which this application already has **RUI_INIT** in progress).  
  
 LUA_UNSUCCESSFUL  
 Primary return code; the verb record supplied was valid, but the verb did not complete successfully.  
  
 LUA_COMMAND_COUNT_ERROR  
  
 Secondary return code, which indicates one of the following errors occurred:  
  
 The verb could not be issued because the application had already reached its maximum number of active sessions. On Windows, an application can have as many as 15,000 sessions active at any time.  
  
 The verb specified the name of an LU pool or the name of an LU in a pool, but all the LUs in the pool are in use.  
  
 LUA_ENCR_DECR_LOAD_ERROR  
  
 Secondary return code; the verb specified a value for **lua_encr_decr_option** other than 0 or 128.  
  
 LUA_INVALID_PROCESS  
  
 Secondary return code; the LU specified by **lua_luname** is in use by another process.  
  
 LUA_LINK_NOT_STARTED  
  
 Secondary return code; the connection to the host has not been started; none of the link services it could use are active.  
  
 LUA_COMM_SUBSYSTEM_ABENDED  
 Primary return code; indicates one of the following conditions:  
  
- The node used by this conversation encountered an ABEND.  
  
- The connection between the transaction program (TP) and the physical unit (PU) 2.1 node has been broken (a LAN error).  
  
- The SnaBase at the TPs computer encountered an ABEND.  
  
  LUA_SESSION_FAILURE  
  Primary return code; a required Host Integration Server component has terminated.  
  
  LUA_LU_COMPONENT_DISCONNECTED  
  
  Secondary return code; indicates that the LUA session failed because of a problem with the link service or with the host LU.  
  
  LUA_INVALID_VERB  
  Primary return code; either the verb code or the operation code, or both, is invalid. The verb did not execute.  
  
  LUA_STACK_TOO_SMALL  
  Primary return code; the stack size of the application is too small to execute the verb. Increase the stack size of your application.  
  
  LUA_COMM_SUBSYSTEM_NOT_LOADED  
  Primary return code; a required component could not be loaded or has terminated while processing the verb. Thus, communication could not take place. Contact the system administrator for corrective action.  
  
  LUA_UNEXPECTED_DOS_ERROR  
  Primary return code; after issuing an operating system call, an unexpected operating system return code was received and is specified in the secondary return code.  
  
## Remarks  
 This verb must be the first LUA verb issued for the session. Until this verb has completed successfully, the only other LUA verb that can be issued for this session is [RUI_TERM](../core/rui-term2.md) (which terminates a pending **RUI_INIT**).  
  
 All other verbs issued on this session must identify the session using one of the following parameters from this verb:  
  
- The session identifier, returned to the application in **lua_sid**.  
  
- The LU name or LU pool name, supplied by the application in the **lua_luname** parameter.  
  
  **RUI_INIT** completes after an ACTLU message is received from the host. If necessary, the verb waits indefinitely. If an ACTLU has already been received prior to **RUI_INIT**, LUA sends a NOTIFY to the host to inform it that the LU is ready for use.  
  
  Neither ACTLU nor NOTIFY is visible to the LUA application.  
  
  After **RUI_INIT** has completed successfully, this session uses the LU for which the session was started. No other LUA session (from this or any other application) can use the LU until **RUI_TERM** is issued, or until an LUA_SESSION_FAILURE primary return code is received.  
  
## Using 3270 LUs  
 To provide 3270 emulator users the ability to use the Emulator Interface Specification (EIS) configuration call with the RUI API, a Host Integration Server extension has been added to the RUI. This extension allows you to use 3270 LUs rather than LUA LUs. If an application sets **lua_resv56[1]** to a nonzero value on the **RUI_INIT** call, 3270 LUs can be used.  
  
## Do Not Release the LU  
 If an application sets **lua_resv56[2]** to a nonzero value on the **RUI_INIT** call, the RUI library will not release the LU when the LU-SSCP session or connection goes away. When this Host Integration Server extension is enabled, the application does not have to issue a new **RUI_INIT** after a session failure or connection failure. When the LU-SSCP session comes back up (the application can use **WinRUIGetLastInitStatus** to detect this), the application can start using it again.  
  
## Support Chunking on this Session  
 If an application sets **lua_resv56[3]** to a nonzero value on the **RUI_INIT** session establishment, this enables a Host Integration Server extension that can change the behavior of **RUI_READ**. The default behavior for an **RUI_READ** call is to truncate data (discarding any data remaining) if the application's data buffer is not large enough to receive all of the data in the RU, returning an error code. When **lua_resv56[3]** is set to a nonzero value on the **RUI_INIT** call, an **RUI_READ** issued where the application's data buffer is not large enough will not result in the RU data being discarded. The **RUI_READ** verb will return success (LUA_OK) for the primary return code and LUA_DATA_INCOMPLETE for the secondary return code. Subsequent **RUI_READ** requests can then be issued to retrieve the data that exceeded the application's data buffer.  
  
## Ignore DACTLUs  
 If an application sets **lua_resv56[4]** to a nonzero value on the **RUI_INIT** session establishment, this enables a Host Integration Server extension, and the RUI library will allow the application to keep hold of the LU if it is recycled at the host (that is, deactivated and reactivated).  
  
> [!NOTE]
>  All other reserved fields must be left blank.  
  
 For more information, see the description of the [sepdcrec](../core/sepdcrec1.md) function in the section of the Software Development Kit (SDK) Help on the 3270 Emulator Interface Specification.  
  
## Encryption  
 Session-level cryptography is implemented through Cryptography Verification (CRV) requests. RUI applications must perform all necessary processing of these requests. For all interfaces other than RUI, CRV requests are rejected with a negative response by Host Integration Server.  
  
 For **RUI_INIT**, the following options are supported:  
  
- **lua_encr_decr_option** = 0  
  
- **lua_encr_decr_option** = 128  
  
  Values from 1 through 127 (ACSRENCR and ACSROECR routines) are not supported.  
  
  The sending application is responsible for padding data to a multiple of eight bytes and for setting the padded data indicator bit in the RH as well as for encryption. The receiving application is responsible for removing the padding after decryption.  
  
## See Also  
 [RUI_TERM](../core/rui-term2.md)   
 [SLI_OPEN](../core/sli-open2.md)