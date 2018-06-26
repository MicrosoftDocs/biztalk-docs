---
title: "SLI_BID2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3f1069d6-2bda-46c6-a52e-18a08fdd73ea
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# SLI_BID
The **SLI_BID** verb notifies the Session Level Interface (SLI) application that a message is waiting to be read using [SLI_RECEIVE](../core/sli-receive2.md). **SLI_BID** also provides the current status of the session to the Windows logical unit application (LUA) application.  
  
 The following structure describes the LUA_COMMON member of the verb control block (VCB) used by SLI_BID.  
  
 The second syntax union describes the **LUA_SPECIFIC** member of the VCB used by **SLI_BID**. Other union members are omitted for clarity.  
  
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
    unsigned char  lua_peek_data[12];  
};  
```  
  
## Members  
 **lua_verb**  
 Supplied parameter. Contains the verb code, LUA_VERB_SLI for SLI verbs.  
  
 **lua_verb_length**  
 Supplied parameter. Specifies the length in bytes of the LUA VCB. It must contain the length of the verb record being issued.  
  
 **lua_prim_rc**  
 Primary return code set by LUA at the completion of the verb. The valid return codes vary depending on the LUA verb issued.  
  
 **lua_sec_rc**  
 Secondary return code set by LUA at the completion of the verb. The valid return codes vary depending on the LUA verb issued.  
  
 **lua_opcode**  
 Supplied parameter. Contains the LUA command code (verb operation code) for the verb to be issued, LUA_OPCODE_SLI_BID.  
  
 **lua_correlator**  
 Supplied parameter. Contains a user-supplied value that links the verb with other user-supplied information. LUA does not use or change this information. This parameter is optional.  
  
 **lua_luname**  
 Supplied parameter. Specifies the ASCII name of the local LU used by the Windows LUA session.  
  
 SLI_BID only requires this parameter if lua_sid is zero.  
  
 This parameter is eight bytes long, padded on the right with spaces (0x20) if the name is shorter than eight characters.  
  
 **lua_extension_list_offset**  
 Not used by **SLI_BID** and should be set to zero.  
  
 **lua_cobol_offset**  
 Not used by LUA in Microsoft® Host Integration Server and should be zero.  
  
 **lua_sid**  
 Supplied parameter. Specifies the session identifier and is returned by [SLI_OPEN](../core/sli-open2.md) and [RUI_INIT](../core/rui-init1.md). Other verbs use this parameter to identify the session used for the command. If other verbs use the **lua_luname** parameter to identify sessions, set the **lua_sid** parameter to zero.  
  
 **lua_max_length**  
 Not used by **SLI_BID** and should be set to zero.  
  
 **lua_data_length**  
 Returned parameter. Specifies the length of data returned in **lua_peek_data**.  
  
 **lua_data_ptr**  
 Pointer to the application-supplied buffer that contains the data to be sent for [SLI_SEND](../core/sli-send2.md) and [RUI_WRITE](../core/rui-write2.md) or that will receive data for [SLI_RECEIVE](../core/sli-receive2.md) and [RUI_READ](../core/rui-read2.md). Not used by other RUI and SLI verbs and should be set to zero.  
  
 **lua_post_handle**  
 Supplied parameter. Used under Microsoft Windows Server if asynchronous notification is to be accomplished by events. This variable contains the handle of the event to be signaled or a window handle.  
  
 For all other environments, this parameter is reserved and should be set to zero.  
  
 **lua_th**  
 Returned parameter. Contains the SNA transmission header (TH) of the message received. Various subparameters are returned for read and bid functions. Its subparameters are as follows:  
  
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
  
 **lua_rh**  
 Returned parameter. Contains the SNA request/response header (RH) of the message sent or received. Its subparameters are as follows:  
  
 lua_rh.rri  
  
 Request-response indicator, one bit.  
  
 lua_rh.ruc  
  
 Request/response unit (RU) category, two bits. The following values are valid:  
  
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
  
 **lua_flag1**  
 Supplied parameter. Contains a data structure containing flags for messages supplied by the application. Its subparameters are as follows:  
  
 lua_flag1.bid_enable  
  
 Bid enable indicator, one bit.  
  
 lua_flag1.close_abend  
  
 Close immediate indicator, one bit.  
  
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
 Returned parameter. Specifies the type of SNA message indicated to `SLI_BID`. Possible values are:  
  
 LUA_MESSAGE_TYPE_LU_DATA  
  
 LUA_MESSAGE_TYPE_SSCP_DATA  
  
 LUA_MESSAGE_TYPE_RSP  
  
 LUA_MESSAGE_TYPE_BID  
  
 LUA_MESSAGE_TYPE_BIND  
  
 LUA_MESSAGE_TYPE_BIS  
  
 LUA_MESSAGE_TYPE_CANCEL  
  
 LUA_MESSAGE_TYPE_CHASE  
  
 LUA_MESSAGE_TYPE_LUSTAT_LU  
  
 LUA_MESSAGE_TYPE_LUSTAT_SSCP  
  
 LUA_MESSAGE_TYPE_QC  
  
 LUA_MESSAGE_TYPE_QEC  
  
 LUA_MESSAGE_TYPE_RELQ  
  
 LUA_MESSAGE_TYPE_RTR  
  
 LUA_MESSAGE_TYPE_SBI  
  
 LUA_MESSAGE_TYPE_SIGNAL  
  
 LUA_MESSAGE_TYPE_STSN  
  
 The SLI receives and responds to the BIND and STSN requests through the LUA interface extension routines.  
  
 LU_DATA, LUSTAT_LU, LUSTAT_SSCP, and SSCP_DATA are not SNA commands.  
  
 **lua_flag2**  
 Returned parameter. Contains flags for messages returned by LUA. Its subparameters are as follows:  
  
 lua_flag2.bid_enable  
  
 Indicates that **SLI_BID** was successfully re-enabled if set to 1.  
  
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
  
 **lua_resv56**  
 Reserved and should be set to zero.  
  
 **lua_encr_decr_option**  
 Not used by **SLI_BID** and should be set to zero.  
  
 **lua_peek_data**  
 The union member of **LUA_SPECIFIC** used by the [RUI_BID](../core/rui-bid1.md)and **SLI_BID** verbs. Returned parameter. Contains up to 12 bytes of the data waiting to be read.  
  
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
  
 LUA_RESERVED_FIELD_NOT_ZERO  
  
 Secondary return code; a reserved parameter for the verb just issued is not set to zero.  
  
 LUA_INVALID_POST_HANDLE  
  
 Secondary return code; for a Windows operating system using events as the asynchronous posting method, the Windows LUA VCB does not contain a valid event handle.  
  
 LUA_VERB_LENGTH_INVALID  
  
 Secondary return code; an LUA verb was issued with the value of **lua_verb_length** unexpected by LUA.  
  
 LUA_STATE_CHECK  
 Primary return code; the verb did not execute because it was issued in an invalid state.  
  
 LUA_NO_SLI_SESSION  
  
 Secondary return code; a session was not open or was down due to an [SLI_CLOSE](../core/sli-close1.md) or session failure when a command was issued.  
  
 LUA_SLI_BID_PENDING  
  
 Secondary return code; an SLI verb was still active when another **SLI_BID** was issued. Only one **SLI_BID** can be active at a time.  
  
 LUA_SESSION_FAILURE  
 Primary return code; an error condition, specified in the secondary return code, caused the session to fail.  
  
 LUA_RECEIVED_UNBIND  
  
 Secondary return code; the primary logical unit (PLU) sent an SNA UNBIND command to the LUA interface when a session was active. As a result, the session was stopped.  
  
 LUA_SLI_LOGIC_ERROR  
  
 Secondary return code; the LUA interface found an internal error in logic.  
  
 LUA_NO_RUI_SESSION  
  
 Secondary return code; no session has been initialized for the LUA verb issued, or some verb other than [SLI_OPEN](../core/sli-open2.md) was issued before the session was initialized.  
  
 LUA_MODE_INCONSISTENCY  
  
 Secondary return code; performing this function is not allowed by the current status. The request sent to the half-session component was not executed even though it was understood and supported. This SNA sense code is also an exception request sense code.  
  
 LUA_RECEIVER_IN_TRANSMIT_MODE  
  
 Secondary return code; either resources needed to handle normal flow data were not available or the state of the half-duplex contention was not received when a normal-flow request was received. The result is a race condition. This SNA sense code is also an exception request sense code.  
  
 LUA_LU_COMPONENT_DISCONNECTED  
  
 Secondary return code; an LU component is unavailable because it is not connected properly. Make sure that the power is on.  
  
 LUA_FUNCTION_NOT_SUPPORTED  
  
 Secondary return code; LUA does not support the requested function. A control character, an RU parameter, or a formatted request code may have specified the function. Specific sense code information is in bytes 2 and 3.  
  
 LUA_CHAINING_ERROR  
  
 Secondary return code; the sequence of the chain indicator settings is in error. An invalid request header or request unit for the receivers current session control or data flow control state was found. Delivery to the half-session component was prevented.  
  
 LUA_BRACKET  
  
 Secondary return code; the sender failed to enforce the session bracket rules. Note that contention and race conditions are exempt from this error. An invalid request header or request unit for the receivers current session control or data flow control state was found. Delivery to the half-session component was prevented.  
  
 LUA_DIRECTION  
  
 Secondary return code; while the half-duplex flip-flop state was NOT_RECEIVE, a request for normal flow was received. An invalid request header or request unit for the receivers current session control or data flow control state was found. Delivery to the half-session component was prevented.  
  
 LUA_DATA_TRAFFIC_QUIESCED  
  
 Secondary return code; a data flow control (DFC) or function management data (FMD) request was received from a half-session that sent either a SHUTC command or QC command, and the DFC or FMD request has not responded to a RELQ command. An invalid request header or request unit for the receivers current session control or data flow control state was found. Delivery to the half-session component was prevented.  
  
 LUA_NO_BEGIN_BRACKET  
  
 Secondary return code; the receiver has already sent a positive response to a BIS command when a BID or an FMD request specifying BBI=BB was received. An invalid request header or request unit for the received current session control or data flow control state was found. Delivery to the half-session component was prevented.  
  
 LUA_IMMEDIATE_REQUEST_MODE_ERROR  
  
 Secondary return code; the request violated the immediate request mode protocol. An invalid header request or request unit for the received current session control or data flow control state was found. Delivery to the half-session component was prevented.  
  
 LUA_QUEUED_RESPONSE_ERROR  
  
 Secondary return code; the request violated the queued response protocol. An invalid header request or request unit for the received current session control or data flow control state was found. Delivery to the half-session component was prevented.  
  
 LUA_ERP_SYNC_EVENT_ERROR  
  
 Secondary return code; a violation of the ERP synchronous event protocol occurred. An invalid header request or request unit for the received current session control or data flow control state was found. Delivery to the half-session component was prevented.  
  
 LUA_RSP_CORRELATION_ERROR  
  
 Secondary return code; a response was sent that does not correspond to a previously received request or a response was received that does not correspond to a previously sent request.  
  
 LUA_RSP_PROTOCOL_ERROR  
  
 Secondary return code; a violation of the response protocol was found in the response received from the primary half-session.  
  
 LUA_BB_NOT_ALLOWED  
  
 Secondary return code; the begin bracket indicator was incorrectly specified. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
 LUA_EB_NOT ALLOWED  
  
 Secondary return code; the end bracket indicator was incorrectly specified. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
 LUA_EXCEPTION_RSP_NOT_ALLOWED  
  
 Secondary return code; when an exception response was not allowed, one was requested. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
 LUA_DEFINITE_RSP_NOT_ALLOWED  
  
 Secondary return code; when a definite response was not allowed, one was requested. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
 LUA_CD_NOT_ALLOWED  
  
 Secondary return code; the change-direction indicator was incorrectly specified. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
 LUA_NO_RESPONSE_NOT_ALLOWED  
  
 Secondary return code; a request other than an EXR contained a "NO RESPONSE" The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
 LUA_CHAINING_NOT_SUPPORTED  
  
 Secondary return code; the chaining indicators were incorrectly specified. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
 LUA_BRACKETS_NOT_SUPPORTED  
  
 Secondary return code; the bracket indicators were incorrectly specified. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
 LUA_CD_NOT_SUPPORTED  
  
 Secondary return code; the change-direction indicator was set, but LUA does not support change-direction for this situation. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
 LUA_INCORRECT_USE_OF_FI  
  
 Secondary return code; the format indicator was incorrectly specified. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
 LUA_ALTERNATE_CODE_NOT_SUPPORTED  
  
 Secondary return code; the code selection indicator was set, but LUA does not support code selection for this session. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
 LUA_INCORRECT_RU_CATEGORY  
  
 Secondary return code; the request unit category indicator was incorrectly specified. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
 LUA_INCORRECT_REQUEST_CODE  
  
 Secondary return code; the request code was incorrectly specified. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
 LUA_INCORRECT_SPEC_OF_SDI_RTI  
  
 Secondary return code; the sense-data-included indicator (SDI) and the response-type-indicator (RTI) were not specified correctly on a response. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
 LUA_INCORRECT_DR1I_DR2I_ERI  
  
 Secondary return code; the definite response 1 indicator (DR1I), the definite response 2 indicator (DR2I), and the exception response indicator (ERI) were specified incorrectly. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
 LUA_INCORRECT_USE_OF_QRI  
  
 Secondary return code; the queued response indicator (QRI) was incorrectly specified. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
 LUA_INCORRECT_USE_OF_EDI  
  
 Secondary return code; the enciphered data indicator (EDI) was incorrectly specified. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
 LUA_INCORRECT_USE_OF_PDI  
  
 Secondary return code; the padded data indicator (PDI) was incorrectly specified. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
 LUA_UNSUCCESSFUL  
 Primary return code; the verb record supplied was valid, but the verb did not complete successfully.  
  
 LUA_VERB_RECORD_SPANS_SEGMENTS  
  
 Secondary return code; the LUA VCB length parameter plus the segment offset is beyond the segment end.  
  
 LUA_NOT_ACTIVE  
  
 Secondary return code; LUA was not active within Microsoft Host Integration Server when an LUA verb was issued.  
  
 LUA_INVALID_PROCESS  
  
 Secondary return code; the session for which an LUA verb was issued is unavailable because another process owns the session.  
  
 LUA_LU_INOPERATIVE  
  
 Secondary return code; a severe error occurred while attempting to stop the session. This LU is unavailable for any LUA requests until an activate logical unit (ACTLU) is received from the host.  
  
 LUA_RECEIVE_CORRELATION_TABLE_FULL  
  
 Secondary return code; the session receive correlation table for the flow requested reached its capacity.  
  
 LUA_NEGATIVE_RESPONSE  
 Primary return code; either LUA sent a negative response to a message received from the primary logical unit (PLU) because an error was found in the message, or the application responded negatively to a chain for which the end-of-chain has arrived.  
  
 LUA_FUNCTION_NOT_SUPPORTED  
  
 Secondary return code; the LUA does not support the requested function. A control character, an RU parameter, or a formatted request code may have specified the function. Specific sense code information is in bytes 2 and 3.  
  
 LUA_DATA_TRAFFIC_RESET  
  
 Secondary return code; a half-session of an active session but with inactive data traffic received a normal flow DFC or FMD request. An invalid request header or request unit for the receivers current session control or data flow control state was found. Delivery to the half-session component was prevented.  
  
 LUA_DATA_TRAFFIC_NOT_RESET  
  
 Secondary return code; while the data traffic state was not reset, the session control request was received. An invalid request header or request unit for the received current session control or data flow control state was found. Delivery to the half-session component was prevented.  
  
 LUA_SC_PROTOCOL_VIOLATION  
  
 Secondary return code; a violation of the session control (SC) protocol occurred. A request (that is permitted only after an SC request and a positive response to that request have been successfully exchanged) was received before the required exchange. Byte 4 of the sense data contains the request code. No user data exists for this sense code. An invalid header request or request unit for the received current session control or data flow control state was found. Delivery to the half-session component was prevented.  
  
 LUA_INVALID_SC_OR_NC_RH  
  
 Secondary return code; the RH of an SC or NC request was invalid.  
  
 LUA_PACING_NOT_SUPPORTED  
  
 Secondary return code; the request contained a pacing indicator when support of pacing for this session does not exist for the receiving half-session or boundary function half-session. The BIND options chosen previously or the architectural rules were violated by **lua_rh** values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
 LUA_NAU_INOPERATIVE  
  
 Secondary return code; the network addressable unit (NAU) is not able to process responses or requests. Delivery to the receiver could not take place for one of the following reasons:  
  
 A path information unit error  
  
 A path outage  
  
 An invalid sequence of requests for activation  
  
 If a path error is received during an active session, that usually means there is no longer a valid path to the session partner.  
  
 LUA_CANCELED  
 Primary return code; the secondary return code gives the reason for canceling the command.  
  
 LUA_TERMINATED  
  
 Secondary return code; the session was terminated when a verb was pending. The verb process has been canceled.  
  
 LUA_IN_PROGRESS  
 Primary return code; an asynchronous command was received but is not completed.  
  
 LUA_STATUS  
 Primary return code; the secondary return code contains SLI status information for the application.  
  
 LUA_READY  
  
 Secondary return code; following a NOT_READY status, this status is issued to notify you that the SLI is ready to process commands.  
  
 LUA_NOT_READY  
  
 Secondary return code; an SNA UNBIND type 0x02 command was received, which means a new BIND is coming.  
  
 If the UNBIND type 0x02 is received after the beginning [SLI_OPEN](../core/sli-open2.md) is complete, the session is suspended until a BIND, optional CRV and STSN, and SDT flows are received. These routines are re-entrant because they have to be called again. The session resumes after the SLI processes the SDT command.  
  
 If the UNBIND type 0x02 is received while SLI_OPEN is still processing, the primary return code is session-failure, not status. Or, the receipt of an SNA CLEAR caused the suspension. Receipt of an SNA SDT will cause the session to resume.  
  
 LUA_INIT_COMPLETE  
  
 Secondary return code; the LUA interface initialized the session while **SLI_OPEN** was processing. LUA applications that issue **SLI_OPEN** with the **lua_open_type_prim_sscp** parameter receive this status on [SLI_RECEIVE](../core/sli-receive2.md) or **SLI_BID**.  
  
 LUA_SESSION_END_REQUESTED  
  
 Secondary return code; the LUA interface received an SNA shutdown command (SHUTD) from the host, which means the host is ready to shut down the session.  
  
 LUA_COMM_SUBSYSTEM_ABENDED  
 Primary return code; indicates one of the following conditions:  
  
 The node used by this conversation encountered an ABEND.  
  
 The connection between the transaction program (TP) and the physical unit (PU) 2.1 node has been broken (a LAN error).  
  
 The SnaBase at the TPs computer encountered an ABEND.  
  
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
 **SLI_BID** does the following:  
  
- Notifies a Windows LUA application that a message is waiting to be read.  
  
- Provides the current session status.  
  
- Provides a preview of the next message that will be read by [SLI_RECEIVE](../core/sli-receive2.md).  
  
   This preview contains a maximum of 12 bytes of information (peek data) that enables the Windows LUA application to define its processing strategy for the data.  
  
  To use **SLI_BID** within a Windows LUA application, issue **SLI_BID**. When the verb completes, it can be reactivated in the following two ways:  
  
- Reissue **SLI_BID**.  
  
- Issue SLI_RECEIVE with lua_flag1_bid_enable set to 1. This issues an SLI_BID that uses the most recently accepted address for the VCB and establishes the active bid.  
  
  Each session can have only one **SLI_BID** at a time.  
  
  If multiple messages are available when a Windows LUA application issues SLI_BID, the data flow with the highest priority is returned. The order in which the data can be returned is as follows:  
  
- SSCP expedited  
  
- LU expedited  
  
- SSCP normal  
  
- LU normal  
  
  If [SLI_RECEIVE](../core/sli-receive2.md) has flags set to read more than one type of message flow, the data returned by **SLI_BID** might be for a flow different than the one for which you actually receive data through **SLI_RECEIVE**. This situation occurs when higher priority data arrives from the host after **SLI_BID** completes processing, but before **SLI_RECEIVE** is issued.  
  
  To ensure that SLI_RECEIVE reads the data, the SLI_BID returned specifies the flow that matches lua_flag2 returned by the completed SLI_BID.  
  
## Session Status Return Values  
 If LUA_STATUS is the primary return code, the secondary return code can be LUA_READY, LUA_NOT_READY, LUA_SESSION_END_REQUESTED, or LUA_INIT_COMPLETE. In addition, if LUA_STATUS is the primary return code, the following parameters are used:  
  
 lua_sec_rc  
  
 lua_sid  
  
 LUA_READY is returned after LUA_NOT_READY status, and indicates that the SLI is again ready to perform all commands.  
  
 LUA_NOT_READY indicates that the SLI session is suspended because the SLI has received either an SNA CLEAR command or an SNA UNBIND command with an 0x02 UNBIND type (UNBIND with BIND forthcoming). Depending on what caused the suspension, the session can be reactivated as follows:  
  
- When the suspension is caused by an SNA CLEAR, receiving an SNA SDT reactivates the session.  
  
- When an SNA UNBIND type BIND forthcoming causes suspension of the session and the [SLI_OPEN](../core/sli-open2.md) that opened the session is completed, the session is suspended until the SLI receives a BIND and SDT command. The session can also optionally receive an STSN command. As a result, user-supplied routines issued with the initial SLI_OPEN must be re-entered because they will be recalled.  
  
  The application can send SSCP data after a CLEAR or UNBIND type BIND forthcoming arrives and before the NOT READY status is read. The application can send and receive SSCP data after reading a NOT READY.  
  
  When an SNA UNBIND type BIND forthcoming arrives before completion of the SLI_OPEN that opened the session, LUA_SESSION_FAILURE (not LUA_STATUS) is the primary return code.  
  
  LUA_SESSION_END_REQUESTED indicates that the application received an SNA SHUTD from the host. The Windows LUA application should issue [SLI_CLOSE](../core/sli-close1.md) to close the session when convenient.  
  
  LUA_INIT_COMPLETE is returned only when lua_init_type for SLI_OPEN is LUA_INIT_TYPE_PRIM_SSCP. The status means that SLI_OPEN has been processed sufficiently to allow SSCP data to now be sent or received.  
  
## Exception Requests  
 If a host application request unit is converted into an EXR, sense data will be returned. When an **SLI_BID** completes with the returned verb parameters set as shown, an EXR conversion occurs.  
  
|Member|Set to|  
|------------|------------|  
|**lua_prim_rc**|OK (0x0000)|  
|**lua_sec_rc**|OK (0x00000000)|  
|**lua_rh.rri**|bit off (request unit)|  
|**lua_rh.sdi**|bit on (includes sense data)|  
  
 Of the seven bytes of data in **lua_peek_data**, bytes 0 through 3 define the error detected. The following table indicates possible sense data and the values of bytes 0 through 3.  
  
|Sense data|Value of bytes 0–3|  
|----------------|------------------------|  
|LUA_MODE_INCONSISTENCY|0x08090000|  
|LUA_BRACKET_RACE_ERROR|0x080B0000|  
|LUA_BB_REJECT_NO_RTR|0x08130000|  
|LUA_RECEIVER_IN_TRANSMIT_MODE|0x081B0000|  
|LUA_CRYPTOGRAPHY_FUNCTION_INOP|0x08480000|  
|LUA_SYNC_EVENT_RESPONSE|0x10010000|  
|LUA_RU_DATA_ERROR|0x10020000|  
|LUA_RU_LENGTH_ERROR|0x10020000|  
|LUA_INCORRECT_SEQUENCE_NUMBER|0x20010000|  
  
 The information returned to bytes 3 through 6 in **lua_peek_data** is determined by the first 3 bytes of the initial request unit that caused the error.  
  
## See Also  
 [RUI_INIT](../core/rui-init1.md)   
 [SLI_CLOSE](../core/sli-close1.md)   
 [SLI_OPEN](../core/sli-open2.md)   
 [SLI_RECEIVE](../core/sli-receive2.md)