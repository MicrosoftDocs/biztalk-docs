---
title: "RUI_READ2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aa095980-a3a8-4c8c-8505-210aaaca17a3
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# RUI_READ
The **RUI_READ** verb receives responses, SNA commands, and data into a Microsoft® Windows® logical unit application (LUA) applications buffer.  
  
 The following structure describes the **LUA_COMMON** member of the verb control block (VCB) used by **RUI_READ**.  
  
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
 Supplied parameter. Contains the LUA command code (verb operation code) for the verb to be issued, LUA_OPCODE_RUI_READ.  
  
 *lua_correlator*  
 Supplied parameter. Contains a user-supplied value that links the verb with other user-supplied information. LUA does not use or change this information. This parameter is optional.  
  
 *lua_luname*  
 Supplied parameter. Specifies the ASCII name of the local LU used by the Windows LUA session.  
  
 **RUI_READ** only requires this parameter if **lua_sid** is zero.  
  
 This parameter is eight bytes long, padded on the right with spaces (0x20) if the name is shorter than eight characters.  
  
 *lua_extension_list_offset*  
 Not used by RUI in Host Integration Server and should be set to zero.  
  
 *lua_cobol_offset*  
 Not used by LUA in Microsoft® Host Integration Server and should be zero.  
  
 *lua_sid*  
 Supplied and returned parameter. Specifies the session identifier and is returned by [SLI_OPEN](../core/sli-open2.md) and [RUI_INIT](../core/rui-init1.md). Other verbs use this parameter to identify the session used for the command. If other verbs use the **lua_luname** parameter to identify sessions, set the **lua_sid** parameter to zero.  
  
 *lua_max_length*  
 Specifies the length of received buffer for **RUI_READ** and [SLI_RECEIVE](../core/sli-receive2.md). Not used by other RUI and SLI verbs and should be set to zero.  
  
 *lua_data_length*  
 Returned parameter. Specifies the length of data returned in **lua_peek_data** for the [RUI_BID](../core/rui-bid1.md) verb.  
  
 *lua_data_ptr*  
 Pointer to the application-supplied buffer that is to receive the data from an **RUI_READ** verb. Both SNA commands and data are placed in this buffer, and they can be in an EBCDIC format.  
  
 When **RUI_READ** is issued, this parameter points to the location to receive the data from the host.  
  
 *lua_post_handle*  
 Supplied parameter. Used under Microsoft Windows Server if asynchronous notification is to be accomplished by events. This variable contains the handle of the event to be signaled or a window handle.  
  
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
 Returned parameter. Contains the SNA request/response header (RH) of the message sent or received. It is set for the write function and returned by the read and bid functions. Its subparameters are as follows:  
  
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
  
 Set **lua_flag1.nowait** to 1 to indicate that you want **RUI_READ** to return immediately whether or not data is available to be read, or set it to zero if you want the verb to wait for data before returning.  
  
 Set **lua_flag1.bid_enable** to 1 to re-enable the most recent [RUI_BID](../core/rui-bid1.md) (equivalent to issuing **RUI_BID** again with exactly the same parameters as before), or set it to zero if you do not want to re-enable **RUI_BID**.  
  
 Re-enabling the previous **RUI_BID** reuses the VCB originally allocated for it, so this VCB must not have been freed or modified.  
  
 Set one or more of the following flags to 1 to indicate from which message flow to read data:  
  
 **lua_flag1.sscp_exp**  
  
 **lua_flag1.lu_exp**  
  
 **lua_flag1.sscp_norm**  
  
 **lua_flag1.lu_norm**  
  
 If more than one flag is set, the highest-priority data available is returned. The order of priorities (highest first) is: SSCP expedited, LU expedited, SSCP normal, LU normal. The equivalent flag in the **lua_flag2** group is set to indicate from which flow the data was read.  
  
 *lua_message_type*  
 Specifies the type of the inbound or outbound SNA commands and data. Returned parameter. Specifies the type of SNA message indicated to **RUI_READ**. Possible values are:  
  
 LUA_MESSAGE_TYPE_LU_DATA  
  
 LUA_MESSAGE_TYPE_SSCP_DATA  
  
 LUA_MESSAGE_TYPE_RQR  
  
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
  
 LUA_MESSAGE_TYPE_RTR  
  
 LUA_MESSAGE_TYPE_SBI  
  
 LUA_MESSAGE_TYPE_SHUTD  
  
 LUA_MESSAGE_TYPE_SIGNAL  
  
 LUA_MESSAGE_TYPE_SDT  
  
 LUA_MESSAGE_TYPE_STSN  
  
 LUA_MESSAGE_TYPE_UNBIND  
  
 LU_DATA, LUSTAT_LU, LUSTAT_SSCP, and SSCP_DATA are not SNA commands.  
  
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
  
 LUA_DATA_INCOMPLETE  
  
 Secondary return code; **RUI_READ** was not able to return all of the data received because the application's data buffer (indicated by **lua_max_length**) was not large enough. Subsequent **RUI_READ** requests can be issued to retrieve the remaining RUI data.  
  
 This is not the default behavior for **RUI_READ** and is only enabled when **lua_resv56[3]** is set to a nonzero value in the verb control block when calling [RUI_INIT](../core/rui-init1.md) during session establishment. For more details, see Remarks.  
  
 LUA_CANCELED  
 Primary return code; the verb did not complete successfully because it was canceled by another verb or by an internal error.  
  
 LUA_PURGED  
  
 Secondary return code; **RUI_READ** has been canceled by [RUI_PURGE](../core/rui-purge2.md).  
  
 LUA_TERMINATED  
  
 Secondary return code; [RUI_TERM](../core/rui-term2.md) was issued while **RUI_READ** was pending.  
  
 LUA_PARAMETER_CHECK  
 Primary return code; the verb did not execute because of a parameter error.  
  
 LUA_BAD_DATA_PTR  
  
 Secondary return code; the **lua_data_ptr** parameter contained an invalid value.  
  
 LUA_BAD_SESSION_ID  
  
 Secondary return code; an invalid value for **lua_sid** was specified in the VCB.  
  
 LUA_BID_ALREADY_ENABLED  
  
 Secondary return code; **lua_flag1.bid_enable** was set to re-enable [RUI_BID](../core/rui-bid1.md) but the previous **RUI_BID** was still in progress.  
  
 LUA_DUPLICATE_READ_FLOW  
  
 Secondary return code; the flow flags in the **lua_flag1** group specified one or more session flows for which **RUI_READ** was already outstanding. Only one **RUI_READ** at a time can be waiting on each session flow.  
  
 LUA_INVALID_FLOW  
  
 Secondary return code; none of the **lua_flag1** flow flags was set. At least one of these flags must be set to 1, to indicate from which flow or flows to read.  
  
 LUA_INVALID_POST_HANDLE  
  
 Secondary return code; for a Windows operating system using events as the asynchronous posting method, the Windows LUA VCB does not contain a valid event handle.  
  
 LUA_NO_PREVIOUS_BID_ENABLED  
  
 Secondary return code; **lua_flag1.bid_enable** was set to re-enable [RUI_BID](../core/rui-bid1.md), but there was no previous **RUI_BID** that could be enabled. (For more information, see Remarks.)  
  
 LUA_RESERVED_FIELD_NOT_ZERO  
  
 Secondary return code; a reserved field in the verb record or a parameter not used by this verb was set to a nonzero value.  
  
 LUA_VERB_LENGTH_INVALID  
  
 Secondary return code; an LUA verb was issued with the value of **lua_verb_length** unexpected by LUA.  
  
 LUA_STATE_CHECK  
 Primary return code; the verb did not execute because it was issued in an invalid state.  
  
 LUA_NO_RUI_SESSION  
  
 Secondary return code; [RUI_INIT](../core/rui-init1.md) has not yet completed successfully for the LU name specified on **RUI_READ**.  
  
 LUA_NEGATIVE_RSP  
 Primary return code; indicates one of the following two cases, which can be distinguished by the secondary return code:  
  
- LUA detected an error in the data received from the host. Instead of passing the received message to the application on **RUI_READ**, LUA discards the message (and the rest of the chain if it is in a chain), and sends a negative response to the host. LUA informs the application on a subsequent **RUI_READ** or [RUI_BID](../core/rui-bid1.md) that a negative response was sent.  
  
- The LUA application previously sent a negative response to a message in the middle of a chain. LUA has purged subsequent messages in this chain, and is now reporting to the application that all messages from the chain have been received and purged.  
  
  LUA_SEC_RC  
  
  Secondary return code; this parameter is a nonzero secondary return code containing the sense code sent to the host on the negative response. This indicates that LUA detected an error in the host data and sent a negative response to the host. For information about interpreting the sense code values that may be returned, see [SNA Considerations Using LUA](./sna-considerations-with-lua1.md).  
  
  A secondary return code of zero indicates that, following a previous [RUI_WRITE](../core/rui-write2.md) of a negative response to a message in the middle of a chain, LUA has now received and discarded all messages from this chain.  
  
  LUA_UNSUCCESSFUL  
  Primary return code; the verb record supplied was valid, but the verb did not complete successfully.  
  
  LUA_DATA_TRUNCATED  
  
  Secondary return code; the **lua_data_length** parameter was smaller than the actual length of data received on the message. Only **lua_data_length** bytes of data were returned to the verb; the remaining data was discarded. Additional parameters are also returned if this secondary return code is obtained.  
  
  LUA_NO_DATA  
  
  Secondary return code; **lua_flag1.nowait** was set to indicate immediate return without waiting for data, and no data was currently available on the specified session flow or flows.  
  
  LUA_INVALID_PROCESS  
  
  Secondary return code; the OS/2 process that issued this verb was not the same process that issued [RUI_INIT](../core/rui-init1.md) for this session. Only the process that started a session can issue verbs on that session.  
  
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
  
  *LUA_STACK_TOO_SMALL*  
  Primary return code; the stack size of the application is too small to execute the verb. Increase the stack size of your application.  
  
  *LUA_COMM_SUBSYSTEM_NOT_LOADED*  
  Primary return code; a required component could not be loaded or has terminated while processing the verb. Thus, communication could not take place. Contact the system administrator for corrective action.  
  
  LUA_UNEXPECTED_DOS_ERROR  
  Primary return code; after issuing an operating system call, an unexpected operating system return code was received and is specified in the secondary return code.  
  
## Remarks  
 [RUI_INIT](../core/rui-init1.md) must have completed successfully before **RUI_READ** is issued.  
  
 While an existing **RUI_READ** is pending, you can issue another **RUI_READ** only if it specifies a different session flow or flows from pending **RUI_READ** verbs. You cannot have more than one **RUI_READ** outstanding for the same session flow.  
  
 You can specify a particular message flow (LU normal, LU expedited, SSCP normal, or SSCP expedited) from which to read data, or you can specify more than one message flow. You can have multiple **RUI_READ** verbs outstanding, provided that no two of them specify the same flow.  
  
 Data is received by the application on one of four session flows. The four session flows, from highest to lowest priority are:  
  
- SSCP expedited  
  
- LU expedited  
  
- SSCP normal  
  
- LU normal  
  
  The data flow type that **RUI_READ** is to process is specified in the **lua_flag1** parameter. The application can also specify whether it wants to look at more than one type of data flow. When multiple flow bits are set, the highest priority is received first. When **RUI_READ** completes processing, **lua_flag2** indicates the specific type of flow for which data has been received by the Windows LUA application.  
  
  If [RUI_BID](../core/rui-bid1.md) successfully completes before an **RUI_READ** is issued, the Windows LUA interface can be instructed to reuse the last **RUI_BID** verbs VCB. To do this, issue the **RUI_READ** with **lua_flag1.bid_enable** set.  
  
  The **lua_flag1.bid_enable** parameter can be used only if the following are true:  
  
- **RUI_BID** has already been issued successfully and has completed.  
  
- The storage allocated for **RUI_BID** has not been freed or modified.  
  
- No other **RUI_BID** is pending.  
  
  When using **lua_flag1.bid_enable**, the **RUI_BID** storage must not be freed because the last **RUI_BID** verbs VCB is used. Also, when using **lua_flag1.bid_enable**, the successful completion of **RUI_BID** will be posted.  
  
  If **RUI_READ** is issued with **lua_flag1.nowait** when no data is available to receive, LUA_NO_DATA will be the secondary return code set by the Windows LUA interface.  
  
  If the data received is longer than **lua_max_length**, it is truncated. Only **lua_max_length** bytes of data are returned. The primary return code LUA_UNSUCCESSFUL and the secondary return code LUA_DATA_TRUNCATED are also returned. The RUI library returns as much data as possible to the application's data buffer, but the remaining data in the RUI is discarded and cannot be extracted on subsequent **RUI_READ** requests. This forces the RUI application to allocate an **RUI_READ** data buffer large enough to handle the full RU size.  
  
  This default behavior can be changed by setting the value of **lua_resv56[3]** to a nonzero value in the verb control block when calling [RUI_INIT](../core/rui-init1.md) during session establishment. In this case, if the data received is longer than **lua_max_length**, an **RUI_READ** request will return a primary return code of LUA_OK and a secondary return code of LUA_DATA_INCOMPLETE. An RUI application can then issue new **RUI_READ** calls and receive the remainder of the data.  
  
  This enhancement has not been adopted as part of the Microsoft Windows Open Services Architecture (WOSA) LUA API standard and differs from the implementation of RUI by IBM.  
  
  After a message has been read using **RUI_READ,** it is removed from the incoming message queue and cannot be accessed again. ([RUI_BID](../core/rui-bid1.md) can be used as a nondestructive read. The application can use it to check the type of data available, but the data remains on the incoming queue and does not need to be used immediately.)  
  
  Pacing can be used on the primary-to-secondary half-session (specified in the host configuration), to protect the LUA application from being flooded with messages. If the LUA application is slow to read messages, Host Integration Server delays the sending of pacing responses to the host to slow it down.  
  
## See Also  
 [RUI_BID](../core/rui-bid1.md)   
 [RUI_INIT](../core/rui-init1.md)   
 [RUI_TERM](../core/rui-term2.md)   
 [RUI_WRITE](../core/rui-write2.md)   
 [SLI_OPEN](../core/sli-open2.md)   
 [SLI_PURGE](../core/sli-purge1.md)   
 [SLI_RECEIVE](../core/sli-receive2.md)   
 [SLI_SEND](../core/sli-send2.md)