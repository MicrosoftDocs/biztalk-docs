---
title: "LUA Secondary Return Codes2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 19d69c5a-c50a-424e-9a87-0e8b9a3fba76
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# LUA Secondary Return Codes
## 0x00000000  
 LUA_SEC_RC_OK  
 No additional information exists for LUA_OK.  
  
## 0x00000001  
 LUA_INVALID_LUNAME  
 An invalid **lua_luname** name was specified.  
  
## 0x00000002  
 LUA_BAD_SESSION_ID  
 An invalid value for **lua_sid** was specified in the verb control block (VCB).  
  
## 0x00000003  
 LUA_DATA_TRUNCATED  
 The data was truncated because the data received was longer than the buffer length specified in **lua_max_length**.  
  
## 0x00000004  
 LUA_BAD_DATA_PTR  
 The **lua_data_ptr** parameter either does not contain a valid pointer or does not point to a read/write segment, and supplied data is required.  
  
## 0x00000005  
 LUA_DATA_LENGTH_ERROR  
 One of the following occurred:  
  
-   The supplied data segment for **SLI_RECEIVE** or **SLI_SEND** is not a read/write data segment as required.  
  
-   The supplied data segment for **SLI_RECEIVE** is not as long as that provided in **lua_max_length**.  
  
-   The supplied data segment for **SLI_SEND** is not as long as that provided in **lua_data_length**.  
  
## 0x00000006  
 LUA_RESERVED_FIELD_NOT_ZERO  
 A reserved parameter for the verb just issued is not set to zero.  
  
## 0x00000007  
 LUA_INVALID_POST_HANDLE  
 For a Windows system using events as the asynchronous posting method, the Windows-based logical unit application (LUA) VCB does not contain a valid event handle.  
  
## 0x0000000C  
 LUA_PURGED  
 **SLI_PURGE** was issued and canceled **SLI_RECEIVE**.  
  
## 0x0000000F  
 LUA_BID_VERB_ERROR  
 The buffer with the **SLI_BID** VCB was released before the **SLI_RECEIVE** with **lua_flag1.bid_enable** set to 1 was issued.  
  
## 0x00000010  
 LUA_NO_PREVIOUS_BID_ENABLED  
 **SLI_BID** was not issued prior to issuing **SLI_RECEIVE** with **bid_enable**.  
  
## 0x00000011  
 LUA_NO_DATA  
 No data was available to read when **SLI_RECEIVE** containing a no-wait parameter was issued.  
  
## 0x00000012  
 LUA_BID_ALREADY_ENABLED  
 **SLI_RECEIVE** was issued with **bid_enable** when **SLI_BID** was already active.  
  
## 0x00000013  
 LUA_VERB_RECORD_SPANS_SEGMENTS  
 The LUA VCB length parameter plus the segment offset is beyond the segment end.  
  
## 0x00000014  
 LUA_INVALID_FLOW  
 The **lua_flag1** flow flags were set incorrectly when a verb was issued as follows:  
  
-   When issuing **SLI_SEND** to send an SNA response, set only one **lua_flag1** flow flag.  
  
-   When issuing **SLI_RECEIVE**, set at least one **lua_flag1** flow flag.  
  
## 0x00000015  
 LUA_NOT_ACTIVE  
 LUA was not active within Microsoft Host Integration Server when an LUA verb was issued.  
  
## 0x00000016  
 LUA_VERB_LENGTH_INVALID  
 An LUA verb was issued with the value of **lua_verb_length** unexpected by the LUA.  
  
## 0x00000019  
 LUA_REQUIRED_FIELD_MISSING  
 The verb that was issued either did not include a data pointer (if the data count was not zero) or did not include an **lua_flag1** flow flag.  
  
## 0x00000030  
 LUA_READY  
 Following a NOT_READY status, this status is issued to notify you that the Session Level Interface (SLI) is ready to process commands.  
  
## 0x00000031  
 LUA_NOT_READY  
 One of the following caused the SLI session to be temporarily suspended:  
  
-   An SNA UNBIND type 0x02 command was received, indicating a new BIND is coming.  
  
     If the UNBIND type 0x02 is received after the beginning **SLI_OPEN** is complete, the session is suspended until a BIND, optional CRV and STSN, and SDT flows are received. These routines are re-entrant because they must be called again. The session resumes after the SLI processes the SDT command. If the UNBIND type 0x02 is received while **SLI_OPEN** is still processing, the primary return code is session-failure, not status.  
  
-   The receipt of an SNA CLEAR caused the suspension.  
  
     Receipt of an SNA SDT will cause the session to resume.  
  
## 0x00000032  
 LUA_INIT_COMPLETE  
 The LUA interface initialized the session while **SLI_OPEN** was processing. LUA applications that issue **SLI_OPEN** with **lua_open_type_prim_sscp** receive this status on **SLI_RECEIVE** or **SLI_BID**.  
  
## 0x00000033  
 LUA_SESSION_END_REQUESTED  
 The LUA interface received an SNA shutdown command (SHUTD) from the host, indicating the host is ready to shut down the session.  
  
## 0x00000034  
 LUA_NO_SLI_SESSION  
 A session was not open or was down due to an **SLI_CLOSE** or session failure when a command was issued.  
  
## 0x00000035  
 LUA_SESSION_ALREADY_OPEN  
 A session is already open for the logical unit (LU) name specified in **SLI_OPEN**.  
  
## 0x00000036  
 LUA_INVALID_OPEN_INIT_TYPE  
 The value in the **lua_init_type** contained in **SLI_OPEN** is invalid.  
  
## 0x00000037  
 LUA_INVALID_OPEN_DATA  
 The **lua_init_type** for the **SLI_OPEN** issued is set to LUA_INIT_TYPE_SEC_IS when the buffer for data does not have a valid INITSELF command.  
  
## 0x00000038  
 LUA_UNEXPECTED_SNA_SEQUENCE  
 Unexpected data or commands were received from the host while **SLI_OPEN** was processing.  
  
## 0x00000039  
 LUA_NEG_RSP_FROM_BIND_ROUTINE  
 The user-supplied SLI_BIND routine responded negatively to the BIND. **SLI_OPEN** ended unsuccessfully.  
  
## 0x0000003B  
 LUA_NEG_RSP_FROM_STSN_ROUTINE  
 The user-supplied SLI STSN routine responded negatively to the STSN. **SLI_OPEN** ended unsuccessfully.  
  
## 0x0000003E  
 LUA_INVALID_OPEN_ROUTINE_TYPE  
 The **lua_open_routine_type** for the **SLI_OPEN** list of extension routines is invalid.  
  
## 0x0000003F  
 LUA_MAX_NUMBER_OF_SENDS  
 The application issued a third **SLI_SEND** before one completed.  
  
## 0x00000040  
 LUA_SEND_ON_FLOW_PENDING  
 An **SLI_SEND** was still outstanding when the application issued another **SLI_SEND** for an SNA flow.  
  
## 0x00000041  
 LUA_INVALID_MESSAGE_TYPE  
 The **lua_message_type** parameter is not recognized by the LUA interface.  
  
## 0x00000042  
 LUA_RECEIVE_ON_FLOW_PENDING  
 An **SLI_RECEIVE** was still outstanding when this application issued another **SLI_RECEIVE** for an SNA flow.  
  
## 0x00000043  
 LUA_DATA_LENGTH_ERROR  
 The application did not provide user-supplied data required by the verb issued. Note that when **SLI_SEND** is issued for an SNA LUSTAT command, status (in four bytes) is required, and that when **SLI_OPEN** is issued with secondary initialization, data is required.  
  
## 0x00000044  
 LUA_CLOSE_PENDING  
 One of the following occurred:  
  
-   A CLOSE_ABEND was still pending when another CLOSE_ABEND was issued. You can issue a CLOSE_ABEND if a CLOSE_NORMAL is pending.  
  
-   Either a CLOSE_ABEND or a CLOSE_NORMAL was still pending when a CLOSE_NORMAL was issued.  
  
## 0x00000046  
 LUA_NEGATIVE_RSP_CHASE  
 A negative response to an SNA CHASE command from the host was received by the LUA interface while **SLI_CLOSE** was being processed. **SLI_CLOSE** continued processing to stop the session.  
  
## 0x00000047  
 LUA_NEGATIVE_RSP_SHUTC  
 A negative response to an SNA SHUTC command from the host was received by the SLI while **SLI_CLOSE** was still being processed. **SLI_CLOSE** continued processing to stop the session.  
  
## 0x00000048  
 LUA_NEGATIVE_RSP_RSHUTD  
 A negative response to an SNA RSHUTD command from the host was received by the LUA interface while **SLI_CLOSE** was being processed. **SLI_CLOSE** continued processing to stop the session.  
  
## 0x0000004A  
 LUA_NO_RECEIVE_TO_PURGE  
 No **SLI_RECEIVE** was outstanding when you issued **SLI_PURGE**. One of two situations caused the problem:  
  
-   **SLI_RECEIVE** completed before **SLI_PURGE** finished processing.  
  
     You can change the application to take care of this problem because it is not an error condition.  
  
-   The **lua_data_ptr** parameter does not correctly point to the **SLI_RECEIVE** you want to purge.  
  
## 0x0000004D  
 LUA_CANCEL_COMMAND_RECEIVED  
 The host sent an SNA CANCEL command to cancel the data chain currently being received by **SLI_RECEIVE**.  
  
## 0x0000004E  
 LUA_RUI_WRITE_FAILURE  
 An unexpected error was posted to the SLI by **RUI_WRITE**.  
  
## 0x00000051  
 LUA_SLI_BID_PENDING  
 An SLI verb was still active when another **SLI_BID** was issued. Only one **SLI_BID** can be active at a time.  
  
## 0x00000052  
 LUA_SLI_PURGE_PENDING  
 An **SLI_PURGE** was still active when another **SLI_PURGE** was issued. Only one **SLI_PURGE** can be active at a time.  
  
## 0x00000053  
 LUA_PROCEDURE_ERROR  
 A host procedure error is indicated by the receipt of an NSPE or NOTIFY message. The return code is posted to **SLI_OPEN** when the retry option is not used. To use the reset option, set **lua_wait** to a value other than zero. The LOGON or INITSELF command will be retried until the host is ready or until you issue **SLI_CLOSE**.  
  
## 0x00000054  
 LUA_INVALID_SLI_ENCR_OPTION  
 The **lua_encr_decr_option** parameter was set to 128 in **SLI_OPEN**, which is not supported for the encryption/decryption processing option.  
  
## 0x00000055  
 LUA_RECEIVED_UNBIND  
 The primary LU sent an SNA UNBIND command to the LUA interface when a session was active. As a result, the session was stopped.  
  
## 0x0000007F  
 LUA_SLI_LOGIC_ERROR  
 The LUA interface found an internal error in logic.  
  
## 0x00000080  
 LUA_TERMINATED  
 The session was terminated when a verb was pending. The verb process has been canceled.  
  
## 0x00000081  
 LUA_NO_RUI_SESSION  
 No session has been initialized for the LUA verb issued, or some verb other than **SLI_OPEN** was issued before the session was initialized.  
  
## 0x00000083  
 LUA_INVALID_PROCESS  
 The session for which a Request Unit Interface (RUI) verb was issued is unavailable because another process owns the session.  
  
## 0x0000008C  
 LUA_LINK_NOT_STARTED  
 The LUA was not able to activate the data link during initialization of the session.  
  
## 0x0000008D  
 LUA_INVALID_ADAPTER  
 The configuration for the data link control (DLC) is in error, or the configuration file is corrupted.  
  
## 0x0000008E  
 LUA_ENCR_DECR_LOAD_ERROR  
 An unexpected return code was received from the OS/2 **DosLoadModule** function while attempting to load the user-provided encryption or decryption dynamic link module.  
  
## 0x0000008F  
 LUA_ENCR_DECR_LOAD_ERROR  
 An unexpected return code was received from the OS/2 **DosGetProcAddr** function while attempting to get the procedure address within the user-provided encryption or decryption dynamic link module.  
  
## 0x000000BE  
 LUA_NEG_NOTIFY_RSP  
 The system services control point (SSCP) responded negatively to a NOTIFY request issued indicating that the secondary LU was capable of a session. The half-session component that received the request understood and supported the request but could not execute it.  
  
## 0x000000FF  
 LUA_LU_INOPERATIVE  
 A severe error occurred while the RUI was attempting to stop the session. This LU is unavailable for any LUA requests until an ACTLU is received from the host.  
  
## 0x08010000  
 LUA_RESOURCE_NOT_AVAILABLE  
 The logical unit, physical unit, link, or link station specified in the request unit is unavailable. This return code is posted to **SLI_OPEN** when a resource is unavailable unless you use the retry option.  
  
 To use the retry option, set **lua_wait** to a value other than zero. The LOGON or INITSELF command will be retried until the host is ready or until you issue **SLI_CLOSE**.  
  
## 0x08050000  
 LUA_SESSION_LIMIT_EXCEEDED  
 The session requested was not activated because a network addressable unit (NAU) is at its session limit.  
  
 This SNA sense code applies to the following requests: BID, CINIT, INIT, and ACTDRM. The code will be posted to **SLI_OPEN** when an NAU is at its limit, unless you use the retry option.  
  
 To use the retry option, set **lua_wait** to a value other than zero. The LOGON or INITSELF command will be retried until the host is ready or until you issue **SLI_CLOSE**.  
  
## 0x08090000  
 LUA_MODE_INCONSISTENCY  
 Performing this function is not allowed by the current status. The request sent to the half-session component was not executed even though it was understood and supported. This SNA sense code is also an exception request sense code.  
  
## 0x08120000  
 LUA_INSUFFICIENT_RESOURCES  
 A temporary condition of insufficient resources caused the request receiver to be unable to perform. The request sent to the half-session component was not executed, even though it was understood and supported.  
  
## 0x081B0000  
 LUA_RECEIVER_IN_TRANSMIT_MODE  
 Either resources needed to handle normal flow data were not available or the state of the half-duplex contention was not received when a normal-flow request was received. The result is a race condition. This SNA sense code is also an exception request sense code.  
  
## 0x08310000  
 LUA_LU_COMPONENT_DISCONNECTED  
 An LU component is unavailable because it is not connected properly. Make sure that the power is on.  
  
## 0x08350001  
 LUA_NEGOTIABLE_BIND_ERROR  
 A negotiable BIND was received, which is only allowed by the SLI when a user-supplied SLI_BIND routine is provided with **SLI_OPEN**.  
  
## 0x08350002  
 LUA_BIND_FM_PROFILE_ERROR  
 Only file management header profiles 3 and 4 are supported by the LUA interface. A file management profile other than 3 or 4 was found on the BIND.  
  
## 0x08350003  
 LUA_BIND_TS_PROFILE_ERROR  
 Only Transmission Service (TS) profiles 3 and 4 are supported by the LUA interface. A TS profile other than 3 or 4 was found on the BIND.  
  
## 0x0835000E  
 LUA_BIND_LU_TYPE_ERROR  
 Only LU 0, LU 1, LU 2, and LU 3 are supported by LUA. An LU other than 0, 1, 2, or 3 was found.  
  
## 0x08570000  
 LUA_SSCP_LU_SESSION_NOT_ACTIVE  
 The required SSCP-LU is inactive. Specific sense code information is in bytes 2 and 3. Valid settings are 0x0000, 0x0001, 0x0002, 0x0003, and 0x0004.  
  
## 0x08780001  
 LUA_RECEIVE_CORRELATION_TABLE_FULL  
 The session receive correlation table for the flow requested reached its capacity.  
  
## 0x08780002  
 LUA_SEND_CORR_TABLE_FULL  
 The session send correlation table for the flow requested reached its capacity.  
  
## 0x087D0000  
 LUA_SESSION_SERVICE_PATH_ERROR  
 A request for session services cannot be rerouted to an SSCP-SSCP session path. Specific sense code information in bytes 2 and 3 gives more information about why the request cannot be rerouted.  
  
## 0x10020000  
 LUA_RU_LENGTH_ERROR  
 The request/response unit (RU) request was an incorrect length (either too short or too long). The RU was not interpreted or processed even though it was delivered to the half-session component. The half-session capabilities do not match. This SNA sense code is also an exception request sense code.  
  
## 0x10030000  
 LUA_FUNCTION_NOT_SUPPORTED  
 The LUA does not support the requested function. A control character, an RU parameter, or a formatted request code may have specified the function. Specific sense code information is in bytes 2 and 3.  
  
## 0x10050121  
 LUA_HDX_BRACKET_STATE_ERROR  
 The existing state error prevented the current request from being sent. The determination was made by a protocol computer.  
  
## 0x10050122  
 LUA_RESPONSE_ALREADY_SENT  
 A response for the chain was already sent so that the current request was not sent. The determination was made by a protocol computer.  
  
## 0x10050123  
 LUA_EXR_SENSE_INCORRECT  
 The application responded negatively to an exception request. The sense code was unacceptable.  
  
## 0x10050124  
 LUA_RESPONSE_OUT_OF_ORDER  
 The current response was not for the oldest request. The determination was made by a protocol computer.  
  
## 0x10050125  
 LUA_CHASE_RESPONSE_REQUIRED  
 A CHASE response was still outstanding when a more recent request was attempted. The determination was made by a protocol computer.  
  
## 0x20020000  
 LUA_CHAINING_ERROR  
 The sequence of the chain indicator settings is in error. An invalid request header or request unit for the receivers current session control or data flow control state was found. Delivery to the half-session component was prevented.  
  
## 0x20030000  
 LUA_BRACKET  
 The sender failed to enforce the session bracket rules. Note that contention and race conditions are exempt from this error. An invalid request header or request unit for the receivers current session control or data flow control state was found. Delivery to the half-session component was prevented.  
  
## 0x20040000  
 LUA_DIRECTION  
 While the half-duplex flip-flop state was NOT_RECEIVE, a request for normal flow was received. An invalid request header or request unit for the receivers current session control or data flow control state was found. Delivery to the half-session component was prevented.  
  
## 0x20050000  
 LUA_DATA_TRAFFIC_RESET  
 A half-session of an active session with inactive data traffic received a normal flow DFC or FMD request. An invalid request header or request unit for the receivers current session control or data flow control state was found. Delivery to the half-session component was prevented.  
  
## 0x20060000  
 LUA_DATA_TRAFFIC_QUIESCED  
 A data flow control (DFC) or function management data (FMD) request was received from a half-session that sent either a SHUTC command or QC command, and the DFC or FMD request has not responded to a RELQ command. An invalid request header or request unit for the receivers current session control or data flow control state was found. Delivery to the half-session component was prevented.  
  
## 0x20070000  
 LUA_DATA_TRAFFIC_NOT_RESET  
 While the data traffic state was not reset, the session control request was received. An invalid request header or request unit for the received current session control or data flow control state was found. Delivery to the half-session component was prevented.  
  
## 0x20080000  
 LUA_NO_BEGIN_BRACKET  
 The receiver has already sent a positive response to a Bracket Initiation Stopped (BIS) command when a BID or an FMD request specifying BBI=BB was received. An invalid request header or request unit for the received current session control or data flow control state was found. Delivery to the half-session component was prevented.  
  
## 0x20090000  
 LUA_SC_PROTOCOL_VIOLATION  
 A violation of the session control (SC) protocol occurred. A request (that is permitted only after an SC request and a positive response to that request have been successfully exchanged) was received before the required exchange. Byte 4 of the sense data contains the request code. No user data exists for this sense code. An invalid header request or request unit for the received current session control or data flow control state was found. Delivery to the half-session component was prevented.  
  
## 0x200A0000  
 LUA_IMMEDIATE_REQUEST_MODE_ERROR  
 The request violated the immediate request mode protocol. An invalid header request or request unit for the received current session control or data flow control state was found. Delivery to the half-session component was prevented.  
  
## 0x200B0000  
 LUA_QUEUED_RESPONSE_ERROR  
 The request violated the queued response protocol. An invalid header request or request unit for the received current session control or data flow control state was found. Delivery to the half-session component was prevented.  
  
## 0x200C0000  
 LUA_ERP_SYNC_EVENT_ERROR  
 A violation of the ERP synchronous event protocol occurred. An invalid header request or request unit for the received current session control or data flow control state was found. Delivery to the half-session component was prevented.  
  
## 0x200D0000  
 LUA_RSP_BEFORE_SENDING_REQ  
 A previously received request has not yet been responded to and an attempt was made in half-duplex send/receive mode to send a normal flow request. An invalid header request or request unit for the received current session control or data flow control state was found. Delivery to the half-session component was prevented.  
  
## 0x200E0000  
 LUA_RSP_CORRELATION_ERROR  
 A response was sent that does not correspond to a previously received request or a response was received that does not correspond to a request sent previously.  
  
## 0x200F0000  
 LUA_RSP_PROTOCOL_ERROR  
 A violation of the response protocol was found in the response received from the primary half-session.  
  
## 0x40010000  
 LUA_INVALID_SC_OR_NC_RH  
 The request/response header (RH) of a session control (SC) or network control (NC) request was invalid.  
  
## 0x40030000  
 LUA_BB_NOT_ALLOWED  
 The begin bracket indicator was incorrectly specified. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
## 0x40040000  
 LUA_EB_NOT_ALLOWED  
 The end bracket indicator was incorrectly specified. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
## 0x40060000  
 LUA_EXCEPTION_RSP_NOT_ALLOWED  
 When an exception response was not allowed, one was requested. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
## 0x40070000  
 LUA_DEFINITE_RSP_NOT_ALLOWED  
 When a definite response was not allowed, one was requested. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
## 0x40080000  
 LUA_PACING_NOT_SUPPORTED  
 The request contained a pacing indicator when support of pacing for this session does not exist for the receiving half-session or boundary function half-session. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
## 0x40090000  
 LUA_CD_NOT_ALLOWED  
 The change-direction indicator was incorrectly specified. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
## 0x400A0000  
 LUA_NO_RESPONSE_NOT_ALLOWED  
 A request other than an EXR contained a NO RESPONSE. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
## 0x400B0000  
 LUA_CHAINING_NOT_SUPPORTED  
 The chaining indicators were incorrectly specified. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
## 0x400C0000  
 LUA_BRACKETS_NOT_SUPPORTED  
 The bracket indicators were incorrectly specified. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
## 0x400D0000  
 LUA_CD_NOT_SUPPORTED  
 The change-direction indicator was set, but LUA does not support change-direction for this situation. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
## 0x400F0000  
 LUA_INCORRECT_USE_OF_FI  
 The format indicator was incorrectly specified. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
## 0x40100000  
 LUA_ALTERNATE_CODE_NOT_SUPPORTED  
 The code selection indicator was set, but LUA does not support code selection for this session. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
## 0x40110000  
 LUA_INCORRECT_RU_CATEGORY  
 The request unit category indicator was incorrectly specified. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
## 0x40120000  
 LUA_INCORRECT_REQUEST_CODE  
 The request code was incorrectly specified. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
## 0x40130000  
 LUA_INCORRECT_SPEC_OF_SDI_RTI  
 The sense-data-included indicator (SDI) and the response-type indicator (RTI) were not specified correctly on a response. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
## 0x40140000  
 LUA_INCORRECT_DR1I_DR2I_ERI  
 The DR1I, the DR2I, and the exception response indicator (ERI) were specified incorrectly. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
## 0x40150000  
 LUA_INCORRECT_USE_OF QRI  
 The queued response indicator (QRI) was incorrectly specified. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
## 0x40160000  
 LUA_INCORRECT_USE_OF_EDI  
 The EDI was incorrectly specified. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
## 0x40170000  
 LUA_INCORRECT_USE_OF_PDI  
 The padded data indicator (PDI) was incorrectly specified. The BIND options chosen previously or the architectural rules were violated by the request header parameter values. Delivery to the half-session component was prevented. The errors are not dependent on the current session state. The senders failure to enforce session rules may have caused the errors.  
  
## 0x80030000  
 LUA_NAU_INOPERATIVE  
 The network addressable unit (NAU) is not able to process responses or requests. Delivery to the receiver could not take place for one of the following reasons:  
  
- A path information unit error  
  
- A path outage  
  
- An invalid sequence of requests for activation  
  
  If a path error is received during an active session that usually means there is no longer a valid path to the session partner.  
  
## 0x80050000  
 LUA_NO_SESSION  
 A request to activate a session is required because no active half-session in the receiving end node for the origination-destination pair exists, or no active boundary function half-session component for the origination-destination pair in a node that supplies the boundary function exists. Delivery of the request could not take place for one of the following reasons:  
  
- A path information unit error  
  
- A path outage  
  
- An invalid sequence of requests for activation  
  
  If a path error is received during an active session that usually indicates there is no longer a valid path to the session partner.