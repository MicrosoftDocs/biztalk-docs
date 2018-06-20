---
title: "SLI_OPEN2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6bb743f8-327c-4bdc-82bc-c26057e91212
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# SLI_OPEN
The **SLI_OPEN** verb transfers control of the specified logical unit (LU) to the Microsoft® Windows® logical unit application (LUA) application. **SLI_OPEN** establishes a session between the system services control point (SSCP) and the specified LU, as well as an LU-LU session.  
  
 The following structure describes the LUA_COMMON member of the verb control block (VCB) used by SLI_OPEN.  
  
 The second syntax union describes the **LUA_SPECIFIC** member of the VCB used by **SLI_OPEN**. Other union members are omitted for clarity.  
  
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
  
```  
  
union LUA_SPECIFIC {  
    struct union SLI_OPEN open;  
};  
  
The SLI_OPEN structure contains the following nested structures and members:  
struct LUA_EXT_ENTRY {  
    unsigned char lua_routine_type;  
    unsigned char lua_module_name[9];  
    unsigned char lua_procedure_name[33];  
} ;  
  
struct SLI_OPEN {  
    unsigned char         lua_init_type;  
    unsigned char         lua_resv65;  
    unsigned short        lua_wait;  
    struct LUA_EXT_ENTRY  lua_open_extension[3];  
    unsigned char         lua_ending_delim;  
} ;  
```  
  
## Members  
 **lua_verb**  
 Supplied parameter. Contains the verb code, LUA_VERB_SLI for Session Level Interface (SLI) verbs.  
  
 **lua_verb_length**  
 Supplied parameter. Specifies the length in bytes of the LUA VCB. It must contain the length of the verb record being issued.  
  
 **lua_prim_rc**  
 Primary return code set by LUA at the completion of the verb. The valid return codes vary depending on the LUA verb issued.  
  
 **lua_sec_rc**  
 Secondary return code set by LUA at the completion of the verb. The valid return codes vary depending on the LUA verb issued.  
  
 **lua_opcode**  
 Supplied parameter. Contains the LUA command code (verb operation code) for the verb to be issued, LUA_OPCODE_SLI_OPEN.  
  
 **lua_correlator**  
 Supplied parameter. Contains a user-supplied value that links the verb with other user-supplied information. LUA does not use or change this information. This parameter is optional.  
  
 **lua_luname**  
 Supplied parameter. Specifies the ASCII name of the local LU used by the Windows LUA session.  
  
 SLI_OPEN requires this parameter.  
  
 This parameter is eight bytes long, padded on the right with spaces (0x20) if the name is shorter than eight characters.  
  
 **lua_extension_list_offset**  
 Supplied parameter. Specifies the offset from the start of the VCB to the extension list of user-supplied dynamic-link libraries (DLLs). The value must be the beginning of a word boundary unless there is no extension list. In this case, the value must be set to zero.  
  
 If this option is not used by SLI_OPEN, this member should be set to zero.  
  
 **lua_cobol_offset**  
 Not used by LUA in Microsoft® Host Integration Server  and should be zero.  
  
 **lua_sid**  
 Returned parameter. Specifies the session identifier.  
  
 **lua_max_length**  
 Not used by **SLI_OPEN** and should be set to zero.  
  
 **lua_data_length**  
 Supplied parameter. Specifies the actual length of the data being sent.  
  
 **lua_data_ptr**  
 Pointer to the application-supplied buffer that contains the data to be sent for **SLI_OPEN**.  
  
 Both SNA commands and data are placed in this buffer, and they can be in an Extended Binary Coded Decimal Interchange Code (EBCDIC) format.  
  
 When SLI_OPEN is issued, this parameter can be one of the following:  
  
- The LOGON message for the SSCP normal flow when the initialization type is secondary with an unformatted LOGON message.  
  
- The request/response unit (RU) for INITSELF. When the initialization type is secondary with INITSELF, the necessary data for the application is provided.  
  
- For all other open types, this field should be set to zero.  
  
  This information is provided by the Windows LUA application.  
  
  **lua_post_handle**  
  Supplied parameter. Used under Microsoft Windows Server if asynchronous notification is to be accomplished by events. This variable contains the handle of the event to be signaled or a window handle.  
  
  **lua_th**  
  Not used by **SLI_OPEN** and should be set to zero.  
  
  **lua_rh**  
  Not used by **SLI_OPEN** and should be set to zero.  
  
  **lua_flag1**  
  Not used by **SLI_OPEN** and should be set to zero.  
  
  **lua_message_type**  
  Not used by **SLI_OPEN** and should be set to zero.  
  
  **lua_flag2**  
  Returned parameter. Contains flags for messages returned by LUA. Its subparameters are as follows:  
  
  lua_flag2.async  
  
  Indicates that the LUA interface verb completed asynchronously if set to 1.  
  
  **lua_resv56**  
  Supplied parameter. Reserved field used by **SLI_OPEN** and [RUI_INIT](../core/rui-init1.md). For more information, see the Remarks section.  
  
  lua_resv56[1]  
  
  Supplied parameter. This parameter must be set to zero.  
  
  lua_resv56[2]  
  
  Supplied parameter. Indicates whether an SLI application can access LUs configured as 3270 LUs, in addition to LUA LUs. If this parameter is set to 1, 3270 LUs can be accessed.  
  
  lua_resv56[3]  
  
  Supplied parameter. Indicates whether incomplete reads are supported. If this parameter is set to 1, incomplete or truncated reads are supported. For more details, see the remarks for [RUI_READ](../core/rui-read2.md).  
  
  **lua_encr_decr_option**  
  Not used by **SLI_OPEN** and should be set to zero.  
  
  **open**  
  The union member of **LUA_SPECIFIC** used by **SLI_OPEN**. A supplied set of parameters contained in an **SLI_OPEN** structure required with **SLI_OPEN**.  
  
  open.lua_init_type  
  
  Supplied parameter. Defines how the LU-LU session is initialized by the Windows LUA interface.  
  
  Valid values are as follows:  
  
  LUA_INIT_TYPE_SEC_IS  
  
  LUA_INIT_TYPE_SEC_LOG  
  
  LUA_INIT_TYPE_PRIM  
  
  LUA_INIT_TYPE_PRIM_SSCP  
  
  open.lua_resv65  
  
  Reserved field.  
  
  open.lua_wait  
  
  Supplied parameter. Represents a secondary retry wait time indicating the number of seconds the Windows LUA interface is to wait before retrying the transmission of the INITSELF or the LOGON message after the host sends any one of these messages:  
  
- A negative response and the secondary return code is one of the following:  
  
   RESOURCE_NOT_AVAILABLE  (0x08010000)SESSION_LIMIT_EXCEEDED (0x08050000) SESSION_SERVICE_PATH_ERROR (0x087D0000)  
  
   Note that SLI_OPEN terminates with an error if lua_wait is set to zero and one of the preceding occurs.  
  
- A network services procedure error (NSPE) message.  
  
- A NOTIFY command, which indicates a procedure error.  
  
  open.lua_open_extension  
  
  Supplied parameter. Contains a list of application-supplied extension DLLs to process the BIND, STSN, and CRV commands.  
  
  open.open_extension.lua_routine_type  
  
  The extension routine type. Legal values are:  
  
  LUA_ROUTINE_TYPE_BIND  
  
  LUA_ROUTINE_TYPE_CRV  
  
  LUA_ROUTINE_TYPE_END (indicates end of extension list)  
  
  LUA_ROUTINE_TYPE_STSN  
  
  open.open_extension.lua_module_name  
  
  Supplied parameter. Provides the ASCII module name for the user-supplied extension DLL. The module name can be up to eight characters long, with the remaining bytes set to 0x00.  
  
  open.open_extension.lua_procedure_name  
  
  Supplied parameter. Provides the procedure name in ASCII for the user-supplied extension DLL. The procedure name can be up to 32 characters long, with the remaining bytes set to 0x00.  
  
  open.lua_ending_delim  
  
  The extension list delimiter.  
  
## Return Codes  
 LUA_OK  
 Primary return code; the verb executed successfully.  
  
 LUA_SEC_OK  
  
 Secondary return code; no additional information exists for LUA_OK.  
  
 LUA_PARAMETER_CHECK  
 Primary return code; the verb did not execute because of a parameter error.  
  
 LUA_INVALID_LUNAME  
  
 Secondary return code; an invalid **lua_luname** name was specified.  
  
 LUA_BAD_SESSION_ID  
  
 Secondary return code; an invalid value for **lua_sid** was specified in the VCB.  
  
 LUA_BAD_DATA_PTR  
  
 Secondary return code; the **lua_data_ptr** parameter either does not contain a valid pointer or does not point to a read/write segment and supplied data is required.  
  
 LUA_DATA_SEGMENT_LENGTH_ERROR  
  
 Secondary return code; one of the following occurred:  
  
- The supplied data segment for [SLI_RECEIVE](../core/sli-receive2.md) or [SLI_SEND](../core/sli-send2.md) is not a read/write data segment as required.  
  
- The supplied data segment for SLI_RECEIVE is not as long as that provided in lua_max_length.  
  
- The supplied data segment for SLI_SEND is not as long as that provided in lua_data_length.  
  
  LUA_RESERVED_FIELD_NOT_ZERO  
  
  Secondary return code; a reserved parameter for the verb just issued is not set to zero.  
  
  LUA_INVALID_POST_HANDLE  
  
  Secondary return code; for a Microsoft Windows operating system using events as the asynchronous posting method, the Windows LUA VCB does not contain a valid event handle.  
  
  LUA_VERB_LENGTH_INVALID  
  
  Secondary return code; an LUA verb was issued with a value for **lua_verb_length** unexpected by LUA.  
  
  LUA_INVALID_OPEN_INIT_TYPE  
  
  Secondary return code; the value in the **lua_init_type** contained in **SLI_OPEN** is invalid.  
  
  LUA_INVALID_OPEN_DATA  
  
  Secondary return code; the **lua_init_type** for the **SLI_OPEN** issued is set to LUA_INIT_TYPE_SEC_IS when the buffer for data does not have a valid INITSELF command.  
  
  LUA_INVALID_OPEN_ROUTINE_TYPE  
  
  Secondary return code; the **lua_open_routine_type** for the **SLI_OPEN** list of extension routines is invalid.  
  
  LUA_DATA_LENGTH_ERROR  
  
  Secondary return code; the application did not provide user-supplied data required by the verb issued. Note that when [SLI_SEND](../core/sli-send2.md) is issued for an SNA LUSTAT command, status (in four bytes) is required, and that when **SLI_OPEN** is issued with secondary initialization, data is required.  
  
  LUA_INVALID_SLI_ENCR_OPTION  
  
  Secondary return code; the **lua_encr_decr_option** parameter was set to 128 in **SLI_OPEN**, which is not supported for the encryption/decryption processing option.  
  
  LUA_STATE_CHECK  
  Primary return code; the verb did not execute because it was issued in an invalid state.  
  
  LUA_NOT_ACTIVE  
  
  Secondary return code; LUA was not active within Microsoft Host Integration Server or SNA Server when an LUA verb was issued.  
  
  LUA_UNEXPECTED_SNA_SEQUENCE  
  
  Secondary return code; unexpected data or commands were received from the host while **SLI_OPEN** was processing.  
  
  LUA_NEG_RSP_FROM_BIND_ROUTINE  
  
  Secondary return code; the user-supplied SLI_BIND routine responded negatively to the BIND. **SLI_OPEN** ended unsuccessfully.  
  
  LUA_NEG_RSP_FROM_STSN_ROUTINE  
  
  Secondary return code; the user-supplied SLI STSN routine responded negatively to the STSN. **SLI_OPEN** ended unsuccessfully.  
  
  LUA_PROCEDURE_ERROR  
  
  Secondary return code; a host procedure error is indicated by the receipt of an NSPE or NOTIFY message. The return code is posted to **SLI_OPEN** when the retry option is not used. To use the reset option, set **lua_wait** to a value other than zero. The LOGON or INITSELF command will be retried until the host is ready or until you issue [SLI_CLOSE](../core/sli-close1.md).  
  
  LUA_RECEIVED_UNBIND  
  
  Secondary return code; the primary logical unit (PLU) sent an SNA UNBIND command to the LUA interface when a session was active. As a result, the session was stopped.  
  
  LUA_SLI_LOGIC_ERROR  
  
  Secondary return code; the LUA interface found an internal error in logic.  
  
  LUA_NO_RUI_SESSION  
  
  Secondary return code; no session has been initialized for the LUA verb issued, or some verb other than **SLI_OPEN** was issued before the session was initialized.  
  
  LUA_RESOURCE_NOT_AVAILABLE  
  
  Secondary return code; the logical unit, physical unit, link, or link station specified in the request unit is unavailable. This return code is posted to **SLI_OPEN** when a resource is unavailable unless you use the retry option.  
  
  To use the retry option, set **lua_wait** to a value other than zero. The LOGON or INITSELF command will be retried until the host is ready or until you issue [SLI_CLOSE](../core/sli-close1.md).  
  
  LUA_SESSION_LIMIT_EXCEEDED  
  
  Secondary return code; the session requested was not activated because an NAU is at its session limit. This SNA sense code applies to the following requests: BID, CINIT, INIT, and ACTDRM.  
  
  The code will be posted to **SLI_OPEN** when an NAU is at its limit, unless you use the RETRY option.  
  
  To use the reset option, set **lua_wait** to a value other than zero. The LOGON or INITSELF command will be retried until the host is ready or until you issue **SLI_CLOSE**.  
  
  LUA_LU_COMPONENT_DISCONNECTED  
  
  Secondary return code; an LU component is unavailable because it is not connected properly. Make sure that the power is on.  
  
  LUA_NEGOTIABLE_BIND_ERROR  
  
  Secondary return code; a negotiable BIND was received, which is only allowed by the SLI when a user-supplied SLI_BIND routine is provided with **SLI_OPEN**.  
  
  LUA_BIND_FM_PROFILE_ERROR  
  
  Secondary return code; only file management header profiles 3 and 4 are supported by the LUA interface. A file management profile other than 3 or 4 was found on the BIND.  
  
  LUA_BIND_TS_PROFILE_ERROR  
  
  Secondary return code; only Transmission Service (TS) profiles 3 and 4 are supported by the LUA interface. A TS profile other than 3 or 4 was found on the BIND.  
  
  LUA_BIND_LU_TYPE_ERROR  
  
  Secondary return code; only LU 0, LU 1, LU 2, and LU 3 are supported by LUA. An LU other than 0, 1, 2, or 3 was found.  
  
  LUA_SSCP_LU_SESSION_NOT_ACTIVE  
  
  Secondary return code; the required SSCP-LU is inactive. Specific sense code information is in bytes 2 and 3. Valid settings are 0x0000, 0x0001, 0x0002, 0x0003, and 0x0004.  
  
  LUA_SESSION_SERVICES_PATH_ERROR  
  
  Secondary return code; a request for session services cannot be rerouted to an SSCP-SSCP session path. Specific sense code information in bytes 2 and 3 gives more information about why the request cannot be rerouted.  
  
  LUA_UNSUCCESSFUL  
  Primary return code; the verb record supplied was valid but the verb did not complete successfully.  
  
  LUA_VERB_RECORD_SPANS_SEGMENTS  
  
  Secondary return code; the LUA VCB length parameter plus the segment offset is beyond the segment end.  
  
  LUA_SESSION_ALREADY_OPEN  
  
  Secondary return code; a session is already open for the LU name specified in **SLI_OPEN**.  
  
  LUA_INVALID_PROCESS  
  
  Secondary return code; the session for which an LUA verb was issued is unavailable because another process owns the session.  
  
  LUA_LINK_NOT_STARTED  
  
  Secondary return code; the LUA was not able to activate the data link during initialization of the session.  
  
  LUA_INVALID_ADAPTER  
  
  Secondary return code; the configuration for the data link control (DLC) is in error, or the configuration file is corrupted.  
  
  LUA_ENCR_DECR_LOAD_ERROR  
  
  Secondary return code; an unexpected return code was received from the OS/2 **DosLoadModule** function while attempting to load the user-provided encryption or decryption dynamic link module.  
  
  LUA_ENCR_DECR_PROC_ERROR  
  
  Secondary return code; an unexpected return code was received from the OS/2 **DosGetProcAddr** function while attempting to get the procedure address within the user-provided encryption or decryption dynamic link module.  
  
  LUA_NEG_NOTIFY_RSP  
  
  Secondary return code; the SSCP responded negatively to a NOTIFY request issued indicating that the secondary LU was capable of a session. The half-session component that received the request understood and supported the request but could not execute it.  
  
  LUA_LU_INOPERATIVE  
  
  Secondary return code; a severe error occurred while the SLI was attempting to stop the session. This LU is unavailable for any LUA requests until an activate logical unit (ACTLU) is received from the host.  
  
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
 For each **SLI_OPEN**, the Windows LUA interface:  
  
- Starts the communication session.  
  
- Reads and verifies a BIND command from the host, and passes it to the application if a BIND extension routine is supplied.  
  
- Writes a BIND response.  
  
- Reads and processes the STSN command and passes it to the application if a BIND extension is supplied (if necessary).  
  
- Writes the STSN response (if necessary).  
  
- Reads the CRV command (if necessary).  
  
- Writes the CRV response (if necessary).  
  
- Reads and processes the SDT command.  
  
- Writes the SDT response.  
  
  The Windows LUA interface does the following additional functions for sessions that issue **SLI_OPEN** with the open type set to LUA_INIT_TYPE_SEC_IS or LUA_INIT_TYPE_SEC_LOG:  
  
- Writes an INITSELF or an unformatted LOGON message.  
  
- Reads and processes an INITSELF response or LOGON message response.  
  
  All SNA message traffic is administered by **SLI_OPEN** through the SDT command response.  
  
  To choose a certain LU configured for Windows LUA, the application sets lua_luname to the LU name in ASCII, padded with trailing spaces if necessary.  
  
  When SLI_OPEN is posted with LUA_OK in the lua_prim_rc parameter, SLI_OPEN successfully completed and the LU-LU data-flow session was established. The application can now issue [SLI_BID](../core/sli-bid2.md), [SLI_CLOSE](../core/sli-close1.md), [SLI_PURGE](../core/sli-purge1.md), [SLI_RECEIVE](../core/sli-receive2.md), and [SLI_SEND](../core/sli-send2.md).  
  
  When SLI_OPEN is posted with a primary return code other than LUA_OK or LUA_IN_PROGRESS, the command did not successfully establish a session.  
  
  When using SLI_OPEN, a Windows LUA application must provide a session initialization type. Valid types are:  
  
- [Secondary with INITSELF](../core/secondary-with-initself2.md)  
  
- [Secondary with an Unformatted LOGON Message](../core/secondary-with-an-unformatted-logon-message2.md)  
  
- [Primary Waiting for a BIND Command](../core/primary-waiting-for-a-bind-command1.md)  
  
- [Primary with SSCP Access](../core/primary-with-sscp-access2.md)  
  
- [Secondary with INITSELF](../core/secondary-with-initself2.md)  
  
- [Secondary with an Unformatted LOGON Message](../core/secondary-with-an-unformatted-logon-message2.md)  
  
- [Primary Waiting for a BIND Command](../core/primary-waiting-for-a-bind-command1.md)  
  
- [Primary with SSCP Access](../core/primary-with-sscp-access2.md)  
  
- [BIND, CRV, and STSN Routines](../core/bind-crv-and-stsn-routines2.md)  
  
- [BIND Example](../core/bind-example1.md)  
  
- [Recovering from SESSION_FAILURE](../core/recovering-from-session-failure2.md)  
  
- [Ending a Pending SLI_OPEN](../core/ending-a-pending-sli-open1.md)  
  
## See Also  
 [RUI_INIT](../core/rui-init1.md)   
 [SLI_RECEIVE](../core/sli-receive2.md)   
 [SLI_SEND](../core/sli-send2.md)