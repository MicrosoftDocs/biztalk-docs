---
title: "RUI_BID1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 601af589-2cac-4594-990c-07ed54749c47
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# RUI_BID
The **RUI_BID** verb notifies the Request Unit Interface (RUI) application that a message is waiting to be read using [RUI_READ](../core/rui-read2.md).  
  
 The following structure describes the **LUA_COMMON** member of the verb control block (VCB) used by **RUI_BID**:  
  
 The second syntax union describes the **LUA_SPECIFIC** member of the verb control block (VCB) used by **RUI_BID**. Other union members are omitted for clarity:  
  
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
union LUA_SPECIFIC {  
    unsigned char lua_peek_data[12];  
};  
```  
  
## Members  
 *lua_verb*  
 Supplied parameter. Contains the verb code, LUA_VERB_RUI for RUI verbs.  
  
 *lua_verb_length*  
 Supplied parameter. Specifies the length in bytes of the logical unit application (LUA) VCB. It must contain the length of the verb record being issued.  
  
 *lua_prim_rc*  
 Primary return code set by LUA at the completion of the verb. The valid return codes vary depending on the LUA verb issued.  
  
 *lua_sec_rc*  
 Secondary return code set by LUA at the completion of the verb. The valid return codes vary depending on the LUA verb issued.  
  
 *lua_opcode*  
 Supplied parameter. Contains the LUA command code (verb operation code) for the verb to be issued, LUA_OPCODE_RUI_BID.  
  
 *lua_correlator*  
 Supplied parameter. Contains a user-supplied value that links the verb with other user-supplied information. LUA does not use or change this information. This parameter is optional.  
  
 *lua_luname*  
 Supplied parameter. Specifies the ASCII name of the local LU used by the Windows LUA session.  
  
 **RUI_BID** only requires this parameter if **lua_sid** is zero.  
  
 This parameter is eight bytes long, padded on the right with spaces (0x20) if the name is shorter than eight characters.  
  
 *lua_extension_list_offset*  
 Not used by RUI in Microsoft® Host Integration Server and should be set to zero.  
  
 *lua_cobol_offset*  
 Not used by LUA in Host Integration Server and should be zero.  
  
 *lua_sid*  
 Supplied parameter. Specifies the session identifier and is returned by [SLI_OPEN](../core/sli-open2.md) and [RUI_INIT](../core/rui-init1.md). Other verbs use this parameter to identify the session used for the command. If other verbs use the **lua_luname** parameter to identify sessions, set the **lua_sid** parameter to zero.  
  
 *lua_max_length*  
 Not used by **RUI_BID** and should be set to zero.  
  
 *lua_data_length*  
 Returned parameter. Specifies the length of data returned in **lua_peek_data** for **RUI_BID**.  
  
 *lua_data_ptr*  
 This parameter is not used and should be set to zero.  
  
 *lua_post_handle*  
 Supplied parameter. Used under Microsoft Windows Server if asynchronous notification is to be accomplished by events. This variable contains the handle of the event to be signaled or a window handle.  
  
 *lua_th*  
 Returned parameter. Contains the SNA transmission header (TH) of the message received. Various subparameters are set for write functions and returned for read and bid functions. Its subparameters are as follows:  
  
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
  
 *lua_message_type*  
 Returned parameter. Specifies the type of SNA message indicated to **RUI_BID**. Possible values are:  
  
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
 Returned parameter. Contains flags for messages returned by LUA. Its subparameters are as follows:  
  
 lua_flag2.bid_enable  
  
 Indicates that **RUI_BID** was successfully re-enabled if set to 1.  
  
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
  
 *lua_peek_data*  
 The union member of **LUA_SPECIFIC** used by the **RUI_BID** and [SLI_BID](../core/sli-bid2.md)verbs. Returned parameter. Contains up to 12 bytes of the data waiting to be read.  
  
## Return Codes  
 LUA_OK  
 Primary return code; the verb executed successfully.  
  
 LUA_CANCELED  
 Primary return code; the verb did not complete successfully because it was canceled by another verb.  
  
 LUA_TERMINATED  
  
 Secondary return code; [RUI_TERM](../core/rui-term2.md) was issued while this verb was pending.  
  
 LUA_PARAMETER_CHECK  
 Primary return code; the verb did not execute because of a parameter error.  
  
 LUA_BAD_SESSION_ID  
  
 Secondary return code; an invalid value for **lua_sid** was specified in the VCB.  
  
 LUA_BID_ALREADY_ENABLED  
  
 Secondary return code; **RUI_BID** was rejected because a previous **RUI_BID** was already outstanding. Only one **RUI_BID** can be outstanding at any one time.  
  
 LUA_INVALID_POST_HANDLE  
  
 Secondary return code; for a Windows operating system using events as the asynchronous posting method, the Windows LUA VCB does not contain a valid event handle.  
  
 LUA_RESERVED_FIELD_NOT_ZERO  
  
 Secondary return code; a reserved field in the verb record, or a parameter not used by this verb, was set to a nonzero value.  
  
 LUA_VERB_LENGTH_INVALID  
  
 Secondary return code; an LUA verb was issued with the value of **lua_verb_length** unexpected by LUA.  
  
 LUA_STATE_CHECK  
 Primary return code; the verb did not execute because it was issued in an invalid state.  
  
 LUA_NO_RUI_SESSION  
  
 Secondary return code; [RUI_INIT](../core/rui-init1.md) has not yet completed successfully for the LU name specified on this verb.  
  
 LUA_UNSUCCESSFUL  
 Primary return code; the verb record supplied was valid, but the verb did not complete successfully.  
  
 LUA_INVALID_PROCESS  
  
 Secondary return code; the process that issued this verb was not the same process that issued **RUI_INIT** for this session. Only the process that started a session can issue verbs on that session.  
  
 LUA_NEGATIVE_RSP  
 Primary return code; LUA detected an error in the data received from the host. Instead of passing the received message to the application on [RUI_READ](../core/rui-read2.md), LUA discards the message (and the rest of the chain if it is in a chain), and sends a negative response to the host.  
  
 LUA informs the application on a subsequent **RUI_READ** or **RUI_BID** that a negative response was sent.  
  
 The secondary return code contains the sense code sent to the host on the negative response. For information about interpreting the sense code values that can be returned, see [SNA Considerations Using LUA](./sna-considerations-with-lua1.md).  
  
 A zero secondary return code indicates that, following a previous [RUI_WRITE](../core/rui-write2.md) of a negative response to a message in the middle of a chain, LUA has now received and discarded all messages from this chain.  
  
 LUA_COMM_SUBSYSTEM_ABENDED  
 Primary return code; indicates one of the following conditions:  
  
- The node used by this conversation encountered an ABEND.  
  
- The connection between the transaction program (TP) and the physical unit (PU) 2.1 node has been broken (a LAN error).  
  
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
 **RUI_BID** is used by applications that require notification that a message is waiting to be read. This allows the application to determine how it will handle the message before issuing [RUI_READ](../core/rui-read2.md).  
  
 When a message is available, **RUI_BID** returns with details of the message flow on which it was received, the message type, the TH and RH of the message, and up to 12 bytes of message data.  
  
 The main difference between **RUI_BID** and **RUI_READ** is that **RUI_BID** allows the application to check the data without removing it from the incoming message queue, so it can be left and accessed later. **RUI_READ** removes the message from the queue, so when the application reads the data it must also process it.  
  
 Note the following when using **RUI_BID**:  
  
- [RUI_INIT](../core/rui-init1.md) must complete successfully before this verb is issued.  
  
- Only one **RUI_BID** can be outstanding at any one time.  
  
- After **RUI_BID** has completed successfully, it can be reissued by setting **lua_flag1.bid_enable** on a subsequent [RUI_READ](../core/rui-read2.md). If the verb is reissued in this way, the application must not free or modify the storage associated with the **RUI_BID** record.  
  
- If a message arrives from the host when **RUI_READ** and **RUI_BID** are both outstanding, **RUI_READ** completes and **RUI_BID** is left in progress.  
  
  Each message that arrives is bid only once. After **RUI_BID** indicates that data is waiting on a particular session flow, the application issues **RUI_READ** to receive the data. Any subsequent **RUI_BID** does not report data arriving on that session flow until the message that was bid has been accepted by issuing **RUI_READ**.  
  
  In general, the **lua_data_length** parameter returned on this verb indicates only the length of data in **lua_peek_data**, not the total length of data on the waiting message (except when a value of less than 12 is returned). The application should ensure that the data length on **RUI_READ** that accepts the data is sufficient to contain the message.  
  
## See Also  
 [RUI_INIT](../core/rui-init1.md)   
 [RUI_READ](../core/rui-read2.md)   
 [RUI_TERM](../core/rui-term2.md)   
 [RUI_WRITE](../core/rui-write2.md)   
 [SLI_OPEN](../core/sli-open2.md)