---
title: "LUA_COMMON1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8c9f6ebc-d2a7-41d1-b0ef-dbb0d949d380
caps.latest.revision: 4
author: MandiOhlinger
manager: anneta
---
# LUA_COMMON
The following structure lists the common data structure parameters used by all the logical unit application (LUA) verbs.  
  
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
} LUA_COMMON;  
```  
  
## Remarks  
  
## Members  
 *lua_verb*  
 Supplied parameter. Contains the verb code, LUA_VERB_RUI for Request Unit Interface (RUI) verbs or LUA_VERB_SLI for Session Level Interface (SLI) verbs. For both of these macros the value is 0x5200.  
  
 *lua_verb_length*  
 Supplied parameter. Specifies the length in bytes of the LUA VCB. It must contain the length of the verb record being issued.  
  
 *lua_prim_rc*  
 Primary return code set by LUA at the completion of the verb. The valid return codes vary depending on the LUA verb issued.  
  
 *lua_sec_rc*  
 Secondary return code set by LUA at the completion of the verb. The valid return codes vary depending on the LUA verb issued.  
  
 *lua_opcode*  
 Supplied parameter. Contains the LUA command code (verb operation code) for the verb to be issued, for example, LUA_OPCODE_RUI_BID for the [RUI_BID](../Topic/RUI_BID2.md) verb.  
  
 *lua_correlator*  
 Supplied parameter. Contains a user-supplied value that links the verb with other user-supplied information. LUA does not use or change this information. This parameter is optional.  
  
 *lua_luname*  
 Supplied parameter. Specifies the ASCII name of the local LU used by the Windows LUA session.  
  
 [SLI_OPEN](../core/sli-open.md) and [RUI_INIT](../Topic/RUI_INIT2.md) require this parameter. Other Windows LUA verbs only require this parameter if **lua_sid** is zero.  
  
 This parameter is eight bytes long, padded on the right with spaces (0x20) if the name is shorter than eight characters.  
  
 *lua_extension_list_offset*  
 Specifies the offset from the start of the VCB to the extension list of user-supplied dynamic-link libraries (DLLs). Not used by RUI in Host Integration Server and should be set to zero.  
  
 *lua_cobol_offset*  
 Offset of the COBOL extension. Not used by LUA in Host Integration Server and should be zero.  
  
 *lua_sid*  
 Supplied and returned parameter. Specifies the session identifier and is returned by [SLI_OPEN](../core/sli-open.md) and [RUI_INIT](../Topic/RUI_INIT2.md). Other verbs use this parameter to identify the session used for the command. If other verbs use the **lua_luname** parameter to identify sessions, set the **lua_sid** parameter to zero.  
  
 *lua_max_length*  
 Specifies the length of received buffer for [RUI_READ](../Topic/RUI_READ1.md)and [SLI_RECEIVE](../Topic/SLI_RECEIVE1.md). For other RUI and SLI verbs, it is not used and should be set to zero.  
  
 *lua_data_length*  
 Returned parameter. Specifies the length of data returned in **lua_peek_data** for the [RUI_BID](../Topic/RUI_BID2.md) verb.  
  
 *lua_data_ptr*  
 Pointer to the application-supplied buffer that contains the data to be sent for [SLI_SEND](../Topic/SLI_SEND1.md) and [RUI_WRITE](../Topic/RUI_WRITE1.md) or that will receive data for **SLI_RECEIVE** and **RUI_READ**. For other RUI and SLI verbs, this parameter is not used and should be set to zero.  
  
 *lua_post_handle*  
 Supplied parameter. Used under Windows if asynchronous notification is to be accomplished by events. This variable contains the handle of the event to be signaled or a window handle.  
  
 *lua_th*  
 Returned parameter. Contains the SNA transmission header (TH) of the message sent or received. Various sub parameters are set for write functions and returned for read and bid functions.  
  
 lua_th.flags_fid  
  
 Format identification type 2, four bits.  
  
 lua_th.flags_mpf  
  
 Segmenting mapping field, two bits.  
  
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
 Returned parameter. Contains the SNA request/response header (RH) of the message sent or received. It is set for the write function and returned by the read and bid functions.  
  
 lua_rh.rri  
  
 Request-response indicator, one bit.  
  
 lua_rh.ruc  
  
 RU category, two bits.  
  
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
 Supplied parameter. Contains a data structure containing flags for messages supplied by the application. This parameter is used by [RUI_BID](../Topic/RUI_BID2.md), [RUI_READ](../Topic/RUI_READ1.md), [RUI_WRITE](../Topic/RUI_WRITE1.md), [SLI_BID](../Topic/SLI_BID1.md), [SLI_RECEIVE](../Topic/SLI_RECEIVE1.md), and [SLI_SEND](../Topic/SLI_SEND1.md). For other LUA verbs, this parameter is not used and should be set to zero.  
  
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
 Specifies the type of the inbound or outbound SNA commands and data. This is a returned parameter for [RUI_INIT](../Topic/RUI_INIT2.md) and [SLI_OPEN](../core/sli-open.md) and a supplied parameter for [SLI_SEND](../Topic/SLI_SEND1.md). For other LUA verbs, this variable is not used and should be set to zero.  
  
 Possible values are:  
  
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
  
 The SLI receives and responds to the BIND, CRV, and STSN requests through the LUA interface extension routines.  
  
 LU_DATA, LUSTAT_LU, LUSTAT_SSCP, and SSCP_DATA are not SNA commands.  
  
 *lua_flag2*  
 Returned parameter. Contains flags for messages returned by LUA. This parameter is returned by [RUI_BID](../Topic/RUI_BID2.md), [RUI_READ](../Topic/RUI_READ1.md), [RUI_WRITE](../Topic/RUI_WRITE1.md), [SLI_BID](../Topic/SLI_BID1.md), [SLI_RECEIVE](../Topic/SLI_RECEIVE1.md), and [SLI_SEND](../Topic/SLI_SEND1.md). For other LUA verbs this parameter is not used and should be set to zero.  
  
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
 Supplied parameter. Reserved field used by [SLI_OPEN](../core/sli-open.md) and [RUI_INIT](../Topic/RUI_INIT2.md). For all other LUA verbs, this parameter is reserved and should be set to zero.  
  
 *lua_encr_decr_option*  
 Field for cryptography options. On **RUI_INIT**, only the following are supported:  
  
-   **lua_encr_decr_option** = 0  
  
-   **lua_encr_decr_option** = 128  
  
 For all other LUA verbs, this parameter is reserved and should be set to zero.