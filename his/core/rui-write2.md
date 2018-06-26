---
title: "RUI_WRITE2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a28c4f31-45be-4c84-826d-a0a31c5c3d9a
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# RUI_WRITE
The **RUI_WRITE** verb sends an SNA request or response unit from the logical unit application (LUA) application to the host over either the LU session or the system services control point (SSCP) session, and sends responses, SNA commands, and data from a Microsoft® Windows® LUA application to the host LU.  
  
 The following structure describes the **LUA_COMMON** member of the verb control block (VCB) used by **RUI_WRITE**.  
  
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
 Supplied parameter. Contains the LUA command code (verb operation code) for the verb to be issued, LUA_OPCODE_RUI_WRITE.  
  
 *lua_correlator*  
 Supplied parameter. Contains a user-supplied value that links the verb with other user-supplied information. LUA does not use or change this information. This parameter is optional.  
  
 *lua_luname*  
 Supplied parameter. Specifies the ASCII name of the local LU used by the Windows LUA session.  
  
 **RUI_WRITE** only requires this parameter if **lua_sid** is zero.  
  
 This parameter is eight bytes long, padded on the right with spaces (0x20) if the name is shorter than eight characters.  
  
 *lua_extension_list_offset*  
 Not used by RUI in Microsoft® Host Integration Server and should be set to zero.  
  
 *lua_cobol_offset*  
 Not used by LUA in Host Integration Server and should be zero.  
  
 *lua_sid*  
 Supplied and returned parameter. Specifies the session identifier and is returned by [SLI_OPEN](../core/sli-open2.md) and [RUI_INIT](../core/rui-init1.md). Other verbs use this parameter to identify the session used for the command. If other verbs use the **lua_luname** parameter to identify sessions, set the **lua_sid** parameter to zero.  
  
 *lua_max_length*  
 Not used by **RUI_WRITE** and should be set to zero.  
  
 *lua_data_length*  
 Returned parameter. Specifies the length of data returned in **lua_peek_data** for the [RUI_BID](../core/rui-bid1.md) verb.  
  
 *lua_data_ptr*  
 Points to the buffer containing the data to be sent to the host by **RUI_WRITE**.  
  
 Both SNA commands and data are placed in this buffer, and they can be in an EBCDIC format.  
  
 *lua_post_handle*  
 Supplied parameter. Used under Microsoft Windows if asynchronous notification is to be accomplished by events. This variable contains the handle of the event to be signaled or a window handle.  
  
 *lua_th*  
 Returned parameter. Contains the SNA transmission header (TH) of the message sent or received. Various subparameters are set for write functions and returned for read and bid functions. Its subparameters are as follows:  
  
 lua_th.flags_fid  
  
 Format identification type 2, four bits.  
  
 lua_th.flags_mpf  
  
 Segmenting mapping field, two bits. Defines the type of data segment. The following values are valid:  
  
 **0x00** Middle segment**0x04** Last segment**0x08** First segment**0x0C** Only segment  
  
 lua_th.flags_odai  
  
 Originating address field–destination address field (OAF–DAF) assignor indicator, one bit.  
  
 lua_th.flags_efi  
  
 Expedited flow indicator, one bit.  
  
 lua_th.daf  
  
 Destination address field (DAF), an unsigned char.  
  
 lua_th.oaf  
  
 Originating address field (OAF), an unsigned char.  
  
 lua_th.snf  
  
 Sequence number field, an unsigned char[2].  
  
 *lua_rh*  
 Returned parameter. Contains the SNA request/response header (RH) of the message sent or received. For the RH for **RUI_WRITE**, all fields except the queued-response indicator (**lua_rh.qri**) and pacing indicator (**lua_rh.pi**) are used. Its subparameters are as follows:  
  
 lua_rh.rri  
  
 Request-response indicator, one bit.  
  
 lua_rh.ruc  
  
 RU category, two bits. The following values are valid:  
  
 **LUA_RH_FMD** (**0x00**) FM data segment**LUA_RH_NC** (**0x20**) Network control**LUA_RH_DFC** (**0x40**) Data flow control**LUA_RH_SC** (**0x60**) Session control  
  
 lua_rh.fi  
  
 Format indicator, one bit.  
  
 lua_rh.sdi  
  
 Sense data included indicator, one bit.  
  
 lua_rh.bci  
  
 Begin chain indicator, one bit.  
  
 lua_rh.eci  
  
 End chain indicator, one bit.  
  
 lua_rh.dr1i  
  
 Definite response 1 indicator, one bit.  
  
 lua_rh.dr2i  
  
 Definite response 2 indicator, one bit.  
  
 lua_rh.ri  
  
 Exception response indicator (for a request), or response type indicator (for a response), one bit.  
  
 lua_rh.qri  
  
 Queued response indicator, one bit.  
  
 lua_rh.pi  
  
 Pacing indicator, one bit.  
  
 lua_rh.bbi  
  
 Begin bracket indicator, one bit.  
  
 lua_rh.ebi  
  
 End bracket indicator, one bit.  
  
 lua_rh.cdi  
  
 Change direction indicator, one bit.  
  
 lua_rh.csi  
  
 Code selection indicator, one bit.  
  
 lua_rh.edi  
  
 Enciphered data indicator, one bit.  
  
 lua_rh.pdi  
  
 Padded data indicator, one bit.  
  
 *lua_flag1*  
 Supplied parameter. Contains a data structure containing flags for messages supplied by the application. Its subparameters are as follows:  
  
 lua_flag1.bid_enable  
  
 Bid enable indicator, one bit.  
  
 lua_flag1.close_abend  
  
 Close immediate indicator, one bit.  
  
 lua_flag1.nowait  
  
 No wait for data flag, one bit.  
  
 lua_flag1.sscp_exp  
  
 SSCP expedited flow, one bit.  
  
 lua_flag1.sscp_norm  
  
 SSCP normal flow, one bit.  
  
 lua_flag1.lu_exp  
  
 LU expedited flow, one bit.  
  
 lua_flag1.lu_norm  
  
 LU normal flow, one bit.  
  
 Set one of the following flags to 1 to indicate on which message flow the data is to be sent:  
  
 **lua_flag1.sscp_exp**  
  
 **lua_flag1.sscp_norm**  
  
 **lua_flag1.lu_exp**  
  
 **lua_flag1.lu_norm**  
  
 *lua_message_type*  
 Not used by **RUI_WRITE** and should be set to zero.  
  
 *lua_flag2*  
 Returned parameter. Contains flags for messages returned by LUA. Its subparameters are as follows:  
  
 lua_flag2.bid_enable  
  
 Indicates that [RUI_BID](../core/rui-bid1.md) was successfully re-enabled if set to 1.  
  
 lua_flag2.async  
  
 Indicates that the LUA interface verb completed asynchronously if set to 1.  
  
 lua_flag2.sscp_exp  
  
 Indicates SSCP expedited flow if set to 1.  
  
 lua_flag2.sscp_norm  
  
 Indicates SSCP normal flow if set to 1.  
  
 lua_flag2.lu_exp  
  
 Indicates LU expedited flow if set to 1.  
  
 lua_flag2.lu_norm  
  
 Indicates LU normal flow if set to 1.  
  
 *lua_resv56*  
 Reserved and should be set to zero.  
  
 *lua_encr_decr_option*  
 Reserved and should be set to zero.  
  
## Return Codes  
 LUA_OK  
 Primary return code; the verb executed successfully.  
  
 LUA_CANCELED  
 Primary return code; the verb did not complete successfully because it was canceled by another verb.  
  
 LUA_TERMINATED  
  
 Secondary return code; the verb was canceled because [RUI_TERM](../core/rui-term2.md) was issued for this session.  
  
 LUA_PARAMETER_CHECK  
 Primary return code; the verb did not execute because of a parameter error.  
  
 LUA_BAD_DATA_PTR  
  
 Secondary return code; the **lua_data_ptr** parameter contained an invalid value.  
  
 LUA_BAD_SESSION_ID  
  
 Secondary return code; an invalid value for **lua_sid** was specified in the VCB.  
  
 LUA_DUPLICATE_WRITE_FLOW  
  
 Secondary return code; **RUI_WRITE** was already outstanding for the session flow specified on this verb (the session flow is specified by setting one of the **lua_flag1** flow flags to 1). Only one **RUI_WRITE** at a time can be outstanding on each session flow.  
  
 LUA_INVALID_FLOW  
  
 Secondary return code; the **lua_flag1.sscp_exp** flow flag was set, indicating that the message should be sent on the SSCP expedited flow. LUA does not allow applications to send data on this flow.  
  
 LUA_INVALID_POST_HANDLE  
  
 Secondary return code; for a Windows operating system using events as the asynchronous posting method, the Windows LUA VCB does not contain a valid event handle.  
  
 LUA_MULTIPLE_WRITE_FLOWS  
  
 Secondary return code; more than one of the **lua_flag1** flow flags was set to 1. One and only one of these flags must be set to 1, to indicate which session flow the data is to be sent on.  
  
 LUA_REQUIRED_FIELD_MISSING  
  
 Secondary return code; indicates one of the following cases:  
  
- None of the **lua_flag1** flow flags was set. One and only one of these flags must be set to 1.  
  
- **RUI_WRITE** was used to send a response, and the response required more data than was supplied.  
  
  LUA_RESERVED_FIELD_NOT_ZERO  
  
  Secondary return code; a reserved field in the verb record or a parameter not used by this verb was set to a nonzero value.  
  
  LUA_VERB_LENGTH_INVALID  
  
  Secondary return code; an LUA verb was issued with the value of **lua_verb_length** unexpected by LUA.  
  
  LUA_STATE_CHECK  
  Primary return code; the verb did not execute because it was issued in an invalid state.  
  
  LUA_MODE_INCONSISTENCY  
  
  Secondary return code; the SNA message sent on **RUI_WRITE** was not valid at this time. This is caused by trying to send data on the LU session before the session is bound. Check the sequence of SNA messages sent.  
  
  LUA_NO_RUI_SESSION  
  
  Secondary return code; [RUI_INIT](../core/rui-init1.md) has not yet completed successfully for the LU name specified on this verb.  
  
  LUA_UNSUCCESSFUL  
  Primary return code; the verb record supplied was valid, but the verb did not complete successfully.  
  
  LUA_FUNCTION_NOT_SUPPORTED  
  
  Secondary return code; indicates one of the following cases:  
  
- The **lua_rh.fi** bit (format indicator) was set to 1, but the first byte of the supplied RU was not a recognized request code.  
  
- The **lua_rh.ruc** parameter (RU category) specified the network control (NC) category; LUA does not allow applications to send requests in this category.  
  
  LUA_INVALID_PROCESS  
  
  Secondary return code; the OS/2 process that issued this verb was not the same process that issued **RUI_INIT** for this session. Only the process that started a session can issue verbs on that session.  
  
  LUA_INVALID_SESSION_PARAMETERS  
  
  Secondary return code; the application used **RUI_WRITE** to send a positive response to a BIND message received from the host. However, Host Integration Server cannot accept the BIND parameters as specified, and has sent a negative response to the host. For more information about the BIND profiles accepted by Host Integration Server, see [SNA Considerations Using LUA](./sna-considerations-with-lua1.md).  
  
  LUA_RSP_CORRELATION_ERROR  
  
  Secondary return code; when using **RUI_WRITE** to send a response, **lua_th.snf** (which indicates the sequence number of the received message being responded to) did not contain a valid value.  
  
  LUA_RU_LENGTH_ERROR  
  
  Secondary return code; the **lua_data_length** parameter contained an invalid value. When sending data on the LU normal flow, the maximum length is as specified in the BIND received from the host; for all other flows the maximum length is 256 bytes.  
  
> [!NOTE]
>  Any other secondary return code is an SNA sense code indicating that the supplied SNA data was invalid or could not be sent. For information about interpreting the SNA sense codes that can be returned, see [SNA Considerations Using LUA](./sna-considerations-with-lua1.md).  
  
 LUA_COMM_SUBSYSTEM_ABENDED  
 Primary return code; indicates one of the following conditions:  
  
- The node used by this conversation encountered an ABEND.  
  
- The connection between the transaction program (TP) and the physical unit (PU) 2.1 node was broken (a LAN error).  
  
- The SnaBase at the TPs computer encountered an ABEND.  
  
  LUA_SESSION_FAILURE  
  Primary return code; a required Host Integration Server component has terminated.  
  
  LUA_LU_COMPONENT_DISCONNECTED  
  
  Secondary return code; indicates that the LUA session has failed because of a problem with the link service or with the host LU.  
  
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
 [RUI_INIT](../core/rui-init1.md) must be issued successfully before this verb is issued.  
  
 When sending an SNA request, all applicable values in the **lua_rh** must be set. Chaining and bracketing are the responsibility of the application.  
  
 When sending a response, the type of response determines the **RUI_WRITE** information required. For all responses, you must:  
  
- Set the selected **lua_rh.rri** flag to 1.  
  
- Provide the sequence number in **lua_th.snf** for the request to which you are responding.  
  
  For multi-chain message responses, the sequence number of the last received chain element must be used. For a response to a multichain message ending with a CANCEL command, the CANCEL command sequence number is used.  
  
  For positive responses that only require the request code, set **lua_rh.ri** to zero (indicating that the response is positive) and **lua_data_length** to zero (indicating that no data is provided). The request code is filled in by the RUI, using the sequence number provided.  
  
  For negative responses, set **lua_rh.ri** to 1, **lua_data_ptr** to the SNA sense code address, and **lua_data_length** to the SNA sense code length (four bytes). The sequence number is used by the RUI to fill in the request code.  
  
  For positive responses to the BIND and STSN commands that require data in the responses, set **lua_data_ptr** to point to the response and set **lua_data_length** to the length of the data provided in **lua_data_ptr**.  
  
  While an existing **RUI_WRITE** is pending, you can issue a second **RUI_WRITE** only if it specifies a different session flow from the pending **RUI_WRITE**. You cannot have more than one **RUI_WRITE** outstanding for the same session flow.  
  
  **RUI_WRITE** can be issued on the SSCP normal flow at any time after a successful [RUI_INIT](../core/rui-init1.md). **RUI_WRITE** verbs on the LU expedited or LU normal flows are permitted only after a BIND has been received, and must abide by the protocols specified on the BIND.  
  
  The successful completion of **RUI_WRITE** indicates that the message was queued successfully to the data link. It does not necessarily indicate that the message was sent successfully, or that the host accepted it.  
  
  Pacing can be used on the secondary-to-primary half-session (specified on the BIND) to prevent the LUA application from sending more data than the local or remote LU can handle. If this is the case, an **RUI_WRITE** on the LU normal flow may be delayed by LUA and may take some time to complete.  
  
## See Also  
 [RUI_INIT](../core/rui-init1.md)   
 [RUI_READ](../core/rui-read2.md)   
 [RUI_TERM](../core/rui-term2.md)   
 [SLI_OPEN](../core/sli-open2.md)   
 [SLI_PURGE](../core/sli-purge1.md)   
 [SLI_RECEIVE](../core/sli-receive2.md)   
 [SLI_SEND](../core/sli-send2.md)