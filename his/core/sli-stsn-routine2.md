---
title: "SLI_STSN_ROUTINE2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9670f01d-906a-4eb4-aec1-281f792007df
caps.latest.revision: 4
---
# SLI_STSN_ROUTINE
The **SLI_STSN_ROUTINE** verb notifies the Microsoft® Windows® logical unit application (LUA) application that an STSN command has come from the host and allows the user-supplied routine to examine the request and formulate a response.  
  
 The following structure describes the LUA_COMMON member of the verb control block (VCB) used by SLI_STSN_ROUTINE.  
  
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
 Supplied parameter. Specifies the length in bytes of the LUA VCB. It must contain the length of the verb record being issued.  
  
 **lua_prim_rc**  
 Primary return code set by LUA at the completion of the verb. The valid return codes vary depending on the LUA verb issued.  
  
 **lua_sec_rc**  
 Secondary return code set by LUA at the completion of the verb. The valid return codes vary depending on the LUA verb issued.  
  
 **lua_opcode**  
 Supplied parameter. Contains the LUA command code (verb operation code) for the verb to be issued, LUA_OPCODE_SLI_STSN_ROUTINE.  
  
 **lua_correlator**  
 Supplied parameter. Contains a user-supplied value that links the verb with other user-supplied information. LUA does not use or change this information. This parameter is optional.  
  
 **lua_luname**  
 Supplied parameter. Specifies the ASCII name of the local LU used by the Windows LUA session.  
  
 SLI_STSN_ROUTINE only requires this parameter if lua_sid is zero.  
  
 This parameter is eight bytes long, padded on the right with spaces (0x20) if the name is shorter than eight characters.  
  
 **lua_extension_list_offset**  
 Not used by **SLI_STSN_ROUTINE** and should be set to zero.  
  
 **lua_cobol_offset**  
 Not used by LUA in Microsoft® Host Integration Server or SNA Server and should be zero.  
  
 **lua_sid**  
 Supplied parameter. Specifies the session identifier and is returned by [SLI_OPEN](../core/sli-open1.md) and [RUI_INIT](../core/rui-init2.md). Other verbs use this parameter to identify the session used for the command. If other verbs use the **lua_luname** parameter to identify sessions, set the **lua_sid** parameter to zero.  
  
 **lua_max_length**  
 Not used by **SLI_STSN_ROUTINE** and should be set to zero.  
  
 **lua_data_length**  
 Returned parameter. Specifies the length of the STSN request/response unit (RU) data returned in the data buffer.  
  
 **lua_data_ptr**  
 For the **SLI_STSN_ROUTINE** this parameter contains the address of the STSN RU.  
  
 **lua_post_handle**  
 Supplied parameter. Used under Microsoft Windows Server if asynchronous notification is to be accomplished by events. This variable contains the handle of the event to be signaled or a window handle.  
  
 For all other environments, this parameter is reserved and should be set to zero.  
  
 **lua_th**  
 Returned parameter. Contains the SNA transmission header (TH) of the message received. Various subparameters are returned for read and bid functions.  
  
 **lua_rh**  
 Returned parameter. Contains the SNA request/response header (RH) of the message sent or received.  
  
 **lua_flag1**  
 Supplied parameter. Contains a data structure containing flags for messages supplied by the application.  
  
 **lua_message_type**  
 Supplied parameter. Specifies the type of SNA data or command sent to the host.  
  
 **lua_flag2**  
 Returned parameter. Contains flags for messages returned by LUA.  
  
 lua_flag2.async  
  
 Indicates that the LUA interface verb completed asynchronously if set to 1.  
  
 lua_flag2.sscp_exp  
  
 Indicates system services control point (SSCP) expedited flow if set to 1.  
  
 lua_flag2.sscp_norm  
  
 Indicates SSCP normal flow if set to 1.  
  
 lua_flag2.lu_exp  
  
 Indicates LU expedited flow if set to 1.  
  
 lua_flag2.lu_norm  
  
 Indicates LU normal flow if set to 1.  
  
 **lua_resv56**  
 Reserved and should be set to zero.  
  
 **lua_encr_decr_option**  
 Not used by **SLI_STSN_ROUTINE** and should be set to zero.  
  
## Return Codes  
 LUA_OK  
 Primary return code; the verb executed successfully.  
  
 LUA_SEC_OK  
  
 Secondary return code; no additional information exists for LUA_OK.  
  
 LUA_NEGATIVE_RSP  
 Primary return code; either the LUA sent a negative response to a message received from the primary logical unit (PLU) because an error was found in the message, or the application responded negatively to a chain for which the end-of-chain has arrived.  
  
## Remarks  
 **SLI_STSN_ROUTINE** provides a mechanism for the Windows LUA application to examine and respond to STSN commands. The Windows LUA notifies the Windows LUA application that an STSN command has been received from the host. This is done through a user-supplied dynamic-link library (DLL). The users DLL examines the STSN request and formulates a response to the request.  
  
 The DLL name for the routine is provided as extensions of the [SLI_OPEN](../core/sli-open1.md) verbs VCB. The lua_extension_list_offset parameter provides the offset from the start of the VCB to the first name in the extension list.  
  
 The Windows LUA interface assigns storage space where the VCB is structured. The VCB of the SLI_STSN_ROUTINE contains lua_th and lua_rh. The address of the STSN RU is specified in lua_data_ptr and the length of the RU is specified in lua_data_length.  
  
 When SLI_STSN_ROUTINE returns to the Windows LUA, processing of the SLI_STSN_ROUTINE is completed. The STSN response should overwrite the STSN RU. When the STSN is accepted, the primary return code should be set to LUA_OK. If the STSN is rejected, the primary return code should be set to LUA_NEGATIVE_RSP and the STSN buffer contains the negative sense code. The lua_data_ptr parameter should not be modified.  
  
 If a negative response is returned from SLI_STSN_ROUTINE, [SLI_OPEN](../core/sli-open1.md) is canceled. The lua_prim_rc of the SLI_OPEN is set to LUA_SESSION_FAILURE, and the lua_sec_rc is set to LUA_NEG_RSP_FROM_STSN_ROUTINE.  
  
## See Also  
 [RUI_INIT](../core/rui-init2.md)   
 [RUI_PURGE](../core/rui-purge1.md)   
 [RUI_READ](../core/rui-read1.md)   
 [RUI_WRITE](../core/rui-write1.md)   
 [SLI_OPEN](../core/sli-open1.md)   
 [SLI_PURGE](../core/sli-purge2.md)   
 [SLI_RECEIVE](../core/sli-receive1.md)   
 [SLI_SEND](../core/sli-send1.md)