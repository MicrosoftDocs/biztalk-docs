---
title: "SLI_SEND_EX2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ca2a9c85-af50-462f-a27d-b9ec489e6faa
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# SLI_SEND_EX
The **SLI_SEND_EX** verb sends responses, SNA commands, and data from a Microsoft® Windows® logical unit application (LUA) application to a host logical unit (LU).  
  
 The SLI_SEND_EX verb also supports inbound chaining. The maximum length of data that can be sent by a single verb is 4,294,967,295 bytes. This is compared to a maximum of 65,535 bytes that can be sent by the SLI_SEND verb.  
  
 The following structure describes the LUA_COMMON member of the verb control block (VCB) used by SLI_SEND_EX.  
  
 The second syntax union below describes the **LUA_SPECIFIC** member of the VCB used by **SLI_SEND_EX**. Other union members are omitted for clarity.  
  
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
union LUA_SPECIFIC {  
    struct SLI_SEND_EX_SPECIFIC {  
        unsigned char lua_sequence_number[2];  
        unsigned long lua_data_length_ex;  
    };  
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
 Supplied parameter. Contains the LUA command code (verb operation code) for the verb to be issued, LUA_OPCODE_SLI_SEND_EX.  
  
 **lua_correlator**  
 Supplied parameter. Contains a user-supplied value that links the verb with other user-supplied information. LUA does not use or change this information. This parameter is optional.  
  
 **lua_luname**  
 Supplied parameter. Specifies the ASCII name of the local LU used by the Windows LUA session.  
  
 SLI_SEND only requires this parameter if lua_sid is zero.  
  
 This parameter is eight bytes long, padded on the right with spaces (0x20) if the name is shorter than eight characters.  
  
 **lua_extension_list_offset**  
 Not used by **SLI_SEND_EX** and should be set to zero.  
  
 **lua_cobol_offset**  
 Not used by LUA in Microsoft® Host Integration Server or SNA Server and should be set to zero.  
  
 **lua_sid**  
 Supplied and returned parameter. Specifies the session identifier and is returned by [SLI_OPEN](../core/sli-open2.md) and [RUI_INIT](../core/rui-init1.md). Other verbs use this parameter to identify the session used for the command. If other verbs use the **lua_luname** parameter to identify sessions, set the **lua_sid** parameter to zero.  
  
 **lua_max_length**  
 Not used by **SLI_SEND_EX** and should be set to zero.  
  
 **lua_data_length**  
 This parameter is reserved and must be set to zero.  
  
 The length of data to be sent is set in the lua_data_length_ex parameter.  
  
 **lua_data_ptr**  
 Pointer to the application-supplied buffer that contains the data to be sent to the host by **SLI_SEND_EX**.  
  
 Both SNA commands and data are placed in this buffer, and they can be in an Extended Binary Coded Decimal Interchange Code (EBCDIC) format.  
  
 **lua_post_handle**  
 Supplied parameter. Used under Microsoft Windows Server if asynchronous notification is to be accomplished by events. This variable contains the handle of the event to be signaled or a window handle.  
  
 **lua_th**  
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
  
 **lua_rh**  
 Supplied parameter. Contains the SNA request/response header (RH) of the message sent or received. It is set for [RUI_WRITE](../core/rui-write2.md) and **SLI_SEND**, and returned by [RUI_READ](../core/rui-read2.md) and [RUI_BID](../core/rui-bid1.md). For the RH for **SLI_SEND_EX**, all fields except the queued-response indicator (**lua_rh.qri**) and pacing indicator (**lua_rh.pi**) are used.  
  
 lua_rh.rri  
  
 Request-response indicator, one bit.  
  
 lua_rh.ruc  
  
 Request/response unit (RU) category, two bits.  
  
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
  
 Set one of the following flags to 1 to indicate on which message flow the data is to be sent:  
  
 lua_flag1.sscp_exp  
  
 lua_flag1.sscp_norm  
  
 lua_flag1.lu_exp  
  
 lua_flag1.lu_norm  
  
 **lua_message_type**  
 Specifies the type of the inbound or outbound SNA commands and data. This is a supplied parameter for **SLI_SEND_EX**.  
  
 Possible values are as follows:  
  
 LUA_MESSAGE_TYPE_LU_DATA  
  
 LUA_MESSAGE_TYPE_SSCP_DATA  
  
 LUA_MESSAGE_TYPE_RSP  
  
 LUA_MESSAGE_TYPE_BID  
  
 LUA_MESSAGE_TYPE_BIS  
  
 LUA_MESSAGE_TYPE_CANCEL  
  
 LUA_MESSAGE_TYPE_CHASE  
  
 LUA_MESSAGE_TYPE_LUSTAT_LU  
  
 LUA_MESSAGE_TYPE_LUSTAT_SSCP  
  
 LUA_MESSAGE_TYPE_QC  
  
 LUA_MESSAGE_TYPE_QEC  
  
 LUA_MESSAGE_TYPE_RELQ  
  
 LUA_MESSAGE_TYPE_RQR  
  
 LUA_MESSAGE_TYPE_RTR  
  
 LUA_MESSAGE_TYPE_SBI  
  
 LUA_MESSAGE_TYPE_SIGNAL  
  
 The SLI receives and responds to the BIND and STSN requests through the LUA interface extension routines.  
  
 LU-DATA, LUSTAT_LU, LUSTAT_SSCP, and SSCP_DATA are not SNA commands.  
  
 **lua_flag2**  
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
  
 **lua_resv56**  
 Reserved and should be set to zero.  
  
 **lua_encr_decr_option**  
 Not used by **SLI_SEND_EX** and should be set to zero.  
  
 **lua_sequence_number**  
 The union member of **LUA_SPECIFIC** used by **SLI_SEND_EX**. Returned parameter. Contains the sequence number for either the first in the chain request unit or the only segment in the chain request unit. Note that this parameter is not byte-reversed.  
  
 **lua_data_length_ex**  
 The union member of **LUA_SPECIFIC** used by **SLI_SEND_EX**. Supplied parameter. Specifies the length of data being sent.  
  
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
  
 LUA_BAD_DATA_PTR  
  
 Secondary return code; the **lua_data_ptr** parameter either does not contain a valid pointer or does not point to a read/write segment and supplied data is required.  
  
 LUA_RESERVED_FIELD_NOT_ZERO  
  
 Secondary return code; a reserved parameter for the verb just issued is not set to zero.  
  
 LUA_INVALID_POST_HANDLE  
  
 Secondary return code; for a Microsoft Windows operating system using events as the asynchronous posting method, the Windows LUA VCB does not contain a valid event handle.  
  
 LUA_INVALID_FLOW  
  
 Secondary return code; the **lua_flag1** flow flags were set incorrectly when a verb was issued:  
  
 When issuing **SLI_SEND_EX** to send an SNA response, set only one **lua_flag1** flow flag.  
  
 When issuing [SLI_RECEIVE_EX](../core/sli-receive-ex2.md), set at least one lua_flag1 flow flag.  
  
 LUA_VERB_LENGTH_INVALID  
  
 Secondary return code; an LUA verb was issued with a value for **lua_verb_length** unexpected by LUA.  
  
 LUA_REQUIRED_FIELD_MISSING  
  
 Secondary return code; the verb that was issued either did not include a data pointer (if the data count was not zero) or did not include an **lua_flag1** flow flag.  
  
 LUA_INVALID_MESSAGE_TYPE  
  
 Secondary return code; the **lua_message_type** parameter is not recognized by the LUA interface.  
  
 LUA_DATA_LENGTH_ERROR  
  
 Secondary return code; the application did not provide user-supplied data required by the verb issued. Note that when **SLI_SEND_EX** is issued for an SNA LUSTAT command, status (in four bytes) is required, and that when [SLI_OPEN](../core/sli-open2.md) is issued with secondary initialization, data is required.  
  
 LUA_STATE_CHECK  
 Primary return code; the verb did not execute because it was issued in an invalid state.  
  
 LUA_NO_SLI_SESSION  
  
 Secondary return code; a session was not open or was down due to an [SLI_CLOSE](../core/sli-close1.md) or session failure when a command was issued.  
  
 LUA_MAX_NUMBER_OF_SENDS  
  
 Secondary return code; the application issued a third **SLI_SEND** or an **SLI_SEND_EX** before one completed.  
  
 LUA_SEND_ON_FLOW_PENDING  
  
 Secondary return code; an **SLI_SEND** or an **SLI_SEND_EX** was still outstanding when the application issued another **SLI_SEND_EX** for an SNA flow.  
  
 LUA_SESSION_FAILURE  
 Primary return code; an error condition, specified in the secondary return code, caused the session to fail.  
  
 LUA_RECEIVED_UNBIND  
  
 Secondary return code; the primary logical unit (PLU) sent an SNA UNBIND command to the LUA interface when a session was active. As a result, the session was stopped.  
  
 LUA_SLI_LOGIC_ERROR  
  
 Secondary return code; the LUA interface found an internal error in logic.  
  
 LUA_NO_RUI_SESSION  
  
 Secondary return code; no session has been initialized for the LUA verb issued, or some verb other than [SLI_OPEN](../core/sli-open2.md) was issued before the session was initialized.  
  
 LUA_LU_COMPONENT_DISCONNECTED  
  
 Secondary return code; an LU component is unavailable because it is not connected properly. Make sure that the power is on.  
  
 LUA_DATA_SEGMENT_LENGTH_ERROR  
  
 Secondary return code; one of the following has occurred:  
  
 The supplied data segment for [SLI_RECEIVE_EX](../core/sli-receive-ex2.md) or **SLI_SEND_EX** is not a read/write data segment as required.  
  
 The supplied data segment for SLI_RECEIVE_EX is not as long as that provided in lua_max_length_ex.  
  
 The supplied data segment for SLI_SEND_EX is not as long as that provided in lua_data_length_ex.  
  
 LUA_VERB_RECORD_SPANS_SEGMENTS  
  
 Secondary return code; the LUA VCB length parameter plus the segment offset is beyond the segment end.  
  
 LUA_NOT_ACTIVE  
  
 Secondary return code; LUA was not active within Microsoft Host Integration Server or SNA Server when an LUA verb was issued.  
  
 LUA_SLI_LOGIC_ERROR  
  
 Secondary return code; the LUA interface found an internal error in logic.  
  
 LUA_INVALID_PROCESS  
  
 Secondary return code; the session for which an LUA verb was issued is unavailable because another OS/2 process owns the session.  
  
 LUA_LU_INOPERATIVE  
  
 Secondary return code; a severe error occurred while the LUA was attempting to stop the session. This LU is unavailable for any LUA requests until an activate logical unit (ACTLU) is received from the host.  
  
 LUA_MODE_INCONSISTENCY  
  
 Secondary return code; performing this function is not allowed by the current status. The request sent to the half-session component was not executed even though it was understood and supported. This SNA sense code is also an exception request sense code.  
  
 LUA_INSUFFICIENT_RESOURCES  
  
 Secondary return code; a temporary condition of insufficient resources caused the request receiver to be unable to perform. The request sent to the half-session component was not executed, even though it was understood and supported.  
  
 LUA_SEND_CORRELATION_TABLE_FULL  
  
 Secondary return code; the session send correlation table for the flow requested reached its capacity.  
  
 LUA_RU_LENGTH_ERROR  
  
 Secondary return code; the RU request was an incorrect length (either too short or too long). The request unit was not interpreted or processed even though it was delivered to the half-session component. The half-session capabilities do not match. This SNA sense code is also an exception request sense code.  
  
 LUA_FUNCTION_NOT_SUPPORTED  
  
 Secondary return code; LUA does not support the requested function. A control character, an RU parameter, or a formatted request code may have specified the function. Specific sense code information is in bytes 2 and 3.  
  
 LUA_HDX_BRACKET_STATE_ERROR  
  
 Secondary return code; the existing state error prevented the current request from being sent. The determination was made by a protocol computer.  
  
 LUA_RESPONSE_ALREADY_SENT  
  
 Secondary return code; a response for the chain was already sent so that the current request was not sent. The determination was made by a protocol computer.  
  
 LUA_EXR_SENSE_INCORRECT  
  
 Secondary return code; the application responded negatively to an exception request. The sense code was unacceptable.  
  
 LUA_RESPONSE_OUT_OF_ORDER  
  
 Secondary return code; the current response was not for the oldest request. The determination was made by a protocol computer.  
  
 LUA_CHAIN_RESPONSE_REQUIRED  
  
 Secondary return code; a CHASE response was still outstanding when a more recent request was attempted. The determination was made by a protocol computer.  
  
 LUA_BRACKET  
  
 Secondary return code; the sender failed to enforce the session bracket rules. Note that contention and race conditions are exempt from this error. An invalid request header or request unit for the receivers current session control or data flow control state was found. Delivery to the half-session component was prevented.  
  
 LUA_DIRECTION  
  
 Secondary return code; while the half-duplex flip-flop state was NOT_RECEIVE, a request for normal flow was received. An invalid request header or request unit for the receivers current session control or data flow control state was found. Delivery to the half-session component was prevented.  
  
 LUA_DATA_TRAFFIC_RESET  
  
 Secondary return code; a half-session of an active session but with inactive data traffic received a normal flow data flow control (DFC) or function management data (FMD) request. An invalid request header or request unit for the receivers current session control or data flow control state was found. Delivery to the half-session component was prevented.  
  
 LUA_DATA_TRAFFIC_QUIESCED  
  
 Secondary return code; a DFC or FMD request was received from a half-session that sent either a SHUTC command or QC command, and the DFC or FMD request has not responded to a RELQ command. An invalid request header or request unit for the receivers current session control or data flow control state was found. Delivery to the half-session component was prevented.  
  
 LUA_DATA_TRAFFIC_NOT_RESET  
  
 Secondary return code; while the data traffic state was not reset, the session control request was received. An invalid request header or request unit for the received current session control or data flow control state was found. Delivery to the half-session component was prevented.  
  
 LUA_NO_BEGIN_BRACKET  
  
 Secondary return code; the receiver has already sent a positive response to a BIS command when a BID or an FMD request specifying BBI=BB was received. An invalid request header or request unit for the received current session control or data flow control state was found. Delivery to the half-session component was prevented.  
  
 LUA_SC_PROTOCOL_VIOLATION  
  
 Secondary return code; a violation of SC protocol occurred. A request (that is permitted only after an SC request and a positive response to that request have been successfully exchanged) was received before the required exchange. Byte 4 of the sense data contains the request code. No user data exists for this sense code. An invalid header request or data flow control state was found. Delivery to the half-session component was prevented.  
  
 LUA_IMMEDIATE_REQUEST_MODE_ERROR  
  
 Secondary return code; the request violated the immediate request mode protocol. An invalid header request or request unit for the received current session control or data flow control state was found. Delivery to the half-session component was prevented.  
  
 LUA_QUEUED_RESPONSE_ERROR  
  
 Secondary return code; the request violated the queued response protocol. An invalid header request or request unit for the received current session control or data flow control state was found. Delivery to the half-session component was prevented.  
  
 LUA_ERP_SYNC_EVENT_ERROR  
  
 Secondary return code; a violation of the ERP synchronous event protocol occurred. An invalid header request or request unit for the received current session control or data flow control state was found. Delivery to the half-session component was prevented.  
  
 LUA_RSP_BEFORE_SENDING_REQ  
  
 Secondary return code; a previously received request has not been responded to yet and an attempt was made in half-duplex send/receive mode to send a normal flow request. An invalid header request or request unit for the received current session control or data flow control state was found. Delivery to the half-session component was prevented.  
  
 LUA_RSP_CORRELATION_ERROR  
  
 Secondary return code; a response was sent that does not correspond to a previously received request or a response was received that does not correspond to a previously sent request.  
  
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
  
 Secondary return code; a request other than an EXR contained a "no response." The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
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
  
 LUA_INCORRECT_REQUEST_CODE  
  
 Secondary return code; the request code was incorrectly specified. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
 LUA_INCORRECT_SPEC_OF_SDI_RTI  
  
 Secondary return code; the SDI and the RTI were not specified correctly on a response. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
 LUA_INCORRECT_DR1I_DR2I_ERI  
  
 Secondary return code; the DR1I, the DR2I, and the ERI were specified incorrectly. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
 LUA_INCORRECT_USE_OF_QRI  
  
 Secondary return code; the queued response indicator was incorrectly specified. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
 LUA_INCORRECT_USE_OF_EDI  
  
 Secondary return code; the EDI was incorrectly specified. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
 LUA_INCORRECT_USE_OF_PDI  
  
 Secondary return code; the PDI was incorrectly specified. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
 LUA_NO_SESSION  
  
 Secondary return code; a request to activate a session is required because no active half-session in the receiving end node for the origination-destination pair exists, or no active boundary function half-session component for the origination-destination pair in a node that supplies the boundary function exists. Delivery of the request could not take place for one of the following reasons:  
  
 A path information unit error  
  
 A path outage  
  
 An invalid sequence of requests for activation  
  
 If a path error is received during an active session, that usually indicates there is no longer a valid path to the session partner.  
  
 LUA_CANCELED  
 Primary return code; the secondary return code gives the reason for canceling the command.  
  
 LUA_TERMINATED  
  
 Secondary return code; the session was terminated when a verb was pending. The verb process has been canceled.  
  
 LUA_IN_PROGRESS  
 Primary return code; an asynchronous command was received but is not completed.  
  
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
 **SLI_SEND_EX** sends responses, SNA commands, and data from the Windows LUA application to a host LU.  
  
 The difference between SLI_SEND_EX and SLI_SEND is that the SLI_SEND_EX verb supports inbound chaining and can send up to a maximum of 4,295 kilobytes (KB) in a single verb request. In contrast, SLI_SEND is limited to sending up to 64 KB in a verb request. A single SLI_SEND_EX or SLI_SEND verb defines a chain. A single SLI_RECEIVE_EX or SLI_RECEIVE verb receives a whole chain.  
  
 A session must already be open to issue SLI_SEND_EX for a particular LU-LU session flow. To send data on the SSCP normal flow prior to the completion of [SLI_OPEN](../core/sli-open2.md), the session must have been initialized as primary with SSCP access. In addition, the session status must be INIT_COMPLETE.  
  
 The settings for lua_message_type determine the type of processing that will be done by SLI_SEND_EX. The following table indicates the parameters to set based on the value of lua_message_type.  
  
|SLI_SEND_EX parameter|LU_DATA<br /><br /> SSCP_DATA|BID<br /><br /> BIS<br /><br /> RTR|CHASE<br /><br /> QC|LUSTAT_LU<br /><br /> LUSTAT_SSCP|QEC<br /><br /> RELQ<br /><br /> SBI<br /><br /> SIGNAL|RQR|RSP|  
|-----------------------------|-----------------------------|-------------------------|------------------|---------------------------------|-------------------------------------|---------|---------|  
|**lua_data**<br />**_length**|Req.|0|0|Req.|0|0|Req. (0 if no data)|  
|**lua_data**<br />**_ptr**|Req. (0 if no data)|0|0|Req.|0|0|Req. (0 if no data)|  
|**lua_flag1 flow flags**|0|0|0|0|0|0|Req. (set one)|  
|**lua_rh**|FI DRL1 DRL2 RI BBI EBI CDI CSI EDI|SDI QRI|SDI QRI EBI CDI|SDI QRI DRL1 DRL2 RI BBI EBI CDI|SDI|0|RRI RI|  
|**lua_th**|0|0|0|0|0|0|SNF|  
  
 The location provided in **lua_data_ptr** and the length provided in **lua_data_length_ex** determine the data that the SLI sends. The data will be chained by the SLI verbs if necessary.  
  
 When sending a response, the type of response determines the SLI_SEND_EX information required. For all responses, you must:  
  
- Set the selected **lua_flag1** flow flag.  
  
- Provide the sequence number in lua_th.snf for the request to which you are responding.  
  
- Set lua_message_type to LUA_MESSAGE_TYPE_RSP.  
  
  For multichain message responses, the sequence number of the last received chain element must be used. For a response to a multichain message ending with a CANCEL command, the CANCEL command sequence number is used.  
  
  For positive responses that only require the request code, set lua_rh.ri to zero (indicating that the response is positive) and lua_data_length to zero (indicating no data is provided). The request code is filled in by the SLI, using the sequence number provided.  
  
  For negative responses in which lua_rh.ri is set to 1, set the lua_data_ptr to the SNA sense code address and the lua_data_length to the SNA sense code length (four bytes). The sequence number is used by the SLI to fill in the request code.  
  
## See Also  
 [RUI_INIT](../core/rui-init1.md)   
 [RUI_READ](../core/rui-read2.md)   
 [RUI_WRITE](../core/rui-write2.md)   
 [SLI_BID](../core/sli-bid2.md)   
 [SLI_CLOSE](../core/sli-close1.md)   
 [SLI_OPEN](../core/sli-open2.md)   
 [SLI_RECEIVE_EX](../core/sli-receive-ex2.md)