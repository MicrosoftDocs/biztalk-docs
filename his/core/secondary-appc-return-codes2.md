---
description: "Learn more about: Secondary APPC Return Codes"
title: "Secondary APPC Return Codes2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Secondary APPC Return Codes

The following table lists each return code by numeric value, along with the associated error message.

| Return code value | Return code       | Error message                                                   |
|-------------------|-------------------|-----------------------------------------------------------------|
| 00000000          | AP_CNOS_ACCEPTED  | APPC accepts the session lines and responsibility as specified. |
| 00000001          | AP_BAD_TP_ID      | The value of **tp_id** did not match a transaction program (TP) identifier assigned by APPC. |
| 00000002          | AP_BAD_CONV_ID    | The value of **conv_id** did not match a conversation identifier assigned by APPC. |
| 00000003          | AP_BAD_LU_ALIAS   | APPC cannot find the specified **lu_alias** among those defined. |
| 000000C4          | AP_RCV_IMMD_BAD_FILL (for a basic conversation)  | The **fill** parameter was set to an invalid value. |
| 00000004          | AP_ALLOCATION_FAILURE_NO_RETRY  | The conversation cannot be allocated because of a permanent condition, such as a configuration error or session protocol error. To determine the error, the system administrator should examine the error log file. Do not retry the allocation until the error has been corrected. |
| 00000005          | AP_ALLOCATION_FAILURE_RETRY  | The conversation could not be allocated because of a temporary condition, such as a link failure. The reason for the failure is logged in the system error log. Retry the allocation. |
| 00000006          | AP_INVALID_DATA_SEGMENT  | The program initiation parameters (PIP) data was longer than the allocated data segment, or the address of the PIP data buffer was wrong. |
| 00000007          | AP_CNOS_NEGOTIATED  | APPC accepts the session limits and responsibility as negotiable by the partner logical unit (LU). Values that can be negotiated are:  **plu_mode_session_limit**, **min_conwinners_source**, **min_conwinners_target**, **responsible**, **drain_target** |
| 000000D7          | AP_BAD_RETURN_STATUS_WITH_DATA   | The specified **rtn_status** value was not recognized by APPC. |
| 00000011          | AP_BAD_CONV_TYPE (for a basic conversation) | The value specified for **conv_type** was invalid. |
| 00000012          | AP_BAD_SYNC_LEVEL   | TThe value specified for **sync_level** was invalid. |
| 00000013          | AP_BAD_SECURITY   | The value specified for **security** was invalid. |
| 00000014          | AP_BAD_RETURN_CONTROL   | The value specified for **rtn_ctl** was invalid. |
| 00000016          | AP_PIP_LEN_INCORRECT   | The value of **pip_dlen** was greater than 32767. |
| 00000017          | AP_NO_USE_OF_SNASVCMG (for a mapped conversation)   | SNASVCMG is not a valid value for **mode_name**. |
| 00000018          | AP_UNKNOWN_PARTNER_MODE   | The value specified for **mode_name** was invalid. |
| 00000031          | AP_CONFIRM_ON_SYNC_LEVEL_NONE   | The local TP attempted to use [CONFIRM](../core/confirm2.md) or [MC_CONFIRM](../core/mc-confirm2.md) in a conversation with a synchronization level of AP_NONE. The synchronization level, established by [ALLOCATE](../core/allocate2.md) or [MC_ALLOCATE](../core/mc-allocate2.md), must be AP_CONFIRM_SYNC_LEVEL. |
| 00000032          | AP_CONFIRM_BAD_STATE   | The conversation was not in SEND state. |
| 00000033          | AP_CONFIRM_NOT_LL_BDY   | The conversation for the local TP was in SEND state, and the local TP did not finish sending a logical record. |
| 00000051          | AP_DEALLOC_BAD_TYPE   | The **dealloc_type** parameter was not set to a valid value. |
| 00000052          | AP_DEALLOC_FLUSH_BAD_STATE   | The conversation was not in SEND state and the TP attempted to flush the send buffer. This attempt occurred because the value of **dealloc_type** was AP_FLUSH or because the value of **dealloc_type** was AP_SYNC_LEVEL and the synchronization level of the conversation was AP_NONE. In either case, the conversation must be in SEND state. |
| 00000053          | AP_DEALLOC_CONFIRM_BAD_STATE   | The conversation was not in SEND state, and the TP attempted to flush the send buffer and send a confirmation request.  |
| 00000055          | AP_DEALLOC_NOT_LL_BDY (for a basic conversation)   | The conversation was in SEND state, and the TP did not finish sending a logical record. The **dealloc_type** parameter was set to AP_SYNC_LEVEL or AP_FLUSH. |
| 00000057          | AP_DEALLOC_LOG_LL_WRONG   | The LL field of the general data stream (GDS) error log variable did not match the actual length of the log data. |
| 00000061          | AP_FLUSH_NOT_SEND_STATE   | The conversation was not in SEND state. |
| 000000A1          | AP_P_TO_R_INVALID_TYPE   | The **ptr_type** parameter was not set to a valid value. |
| 000000A2          | AP_P_TO_R_NOT_LL_BDY   | The local TP did not finish sending a logical record. |
| 000000A3          | AP_P_TO_R_NOT_SEND_STATE   | The conversation was not in SEND state. |
| 000000B1          | AP_RCV_AND_WAIT_BAD_STATE   | The conversation was not in RECEIVE or SEND state when the TP issued this verb. |
| 000000B2          | AP_RCV_AND_WAIT_NOT_LL_BDY (for a basic conversation)   | The conversation was in SEND state; the TP began but did not finish sending a logical record. |
| 000000B5          | AP_RCV_AND_WAIT_BAD_FILL (for a basic conversation)    | The **fill** parameter was set to an invalid value. |
| 000000C1          | AP_RCV_IMMD_BAD_STATE    | The conversation was not in RECEIVE state. |
| 000000D1          | AP_RCV_AND_POST_BAD_STATE   | The conversation was not in RECEIVE or SEND state when the TP issued this verb.  |
| 000000D2          | AP_RCV_AND_POST_NOT_LL_BDY   | The conversation was in SEND state; the TP began but did not finish sending a logical record. |
| 000000D5          | AP_RCV_AND_POST_BAD_FILL   | The **fill** parameter was set to an invalid value. |
| 000000D6          | AP_INVALID_SEMAPHORE_HANDLE   | The address of the RAM semaphore or system semaphore handle was invalid. **NOTE**: APPC cannot trap all invalid semaphore handles. If the TP passes a bad RAM semaphore handle, a protection violation results. |
| 000000D7          | AP_BAD_RETURN_STATUS_WITH_DATA   | The specified **rtn_status** value was not recognized by APPC. |
| 000000E1          | AP_R_T_S_BAD_STATE   | The conversation is not in an allowed state when the TP issued this verb. |
| 000000F1          | AP_BAD_LL (for a basic conversation)   | The logical record length field of a logical record contained an invalid value — 0x0000, 0x0001, 0x8000, or 0x8001. See [About Transaction Programs](./transaction-programs-overview1.md) for information on logical records. |
| 000000F2          | AP_SEND_DATA_NOT_SEND_STATE   | The local TP issued [SEND_DATA](../core/send-data1.md) or [MC_SEND_DATA](../core/mc-send-data1.md), but the conversation was not in SEND state. |
| 000000F5          | AP_SEND_DATA_CONFIRM_ON_SYNC_NONE   | The type CONFIRM is not permitted for a conversation that was allocated with a **sync_level** of NONE. |
| 000000F6          | AP_SEND_DATA_NOT_LL_BDY (for a basic conversation)   | The TP started but did not finish sending a logical record. This occurs only when **type** is one of the following:  AP_SEND_DATA_CONFIRM, AP_SEND_DATA_DEALLOC_FLUSH, AP_SEND_DATA_DEALLOC_SYNC_LEVEL, AP_SEND_DATA_P_TO_R_FLUSH, AP_SEND_DATA_P_TO_R_SYNC_LEVEL |
| 00000102          | AP_SEND_ERROR_LOG_LL_WRONG (for a basic conversation)   | The LL field of the error log GDS variable did not match the actual length of the data. |
| 00000103          | AP_SEND_ERROR_BAD_TYPE (for a basic conversation) | The value of **err_type** was invalid. |
| 00000105          | AP_BAD_ERROR_DIRECTION  | The specified **err_dir** was not recognized by APPC. |
| 00000150          | AP_CNOS_IMPLICIT_PARALLEL |  APPC does not permit a program to change the session limit for a mode other than SNASVCMG mode for the implicit partner template when the template specifies parallel sessions. (The term "template" is used because many of the actual values are yet to be filled in.) |
| 00000151          | AP_CANT_RAISE_LIMITS | APPC does not permit setting session limits to a nonzero value unless the limits currently are zero. |
| 00000152          | AP_AUTOACT_EXCEEDS_SESSLIM | On the [CNOS](../core/cnos2.md) verb, the value for **auto_activate** is greater than the value for **partner_lu_mode_session_limit**. |
| 00000153          | AP_ALL_MODE_MUST_RESET | APPC does not permit a nonzero session limit when **mode_name_select** indicates ALL. |
| 00000154          | AP_BAD_SNASVCMG_LIMITS | Your program specified invalid settings for the **partner_lu_mode_session_limit**, **min_conwinners_source**, or **min_conwinners_target** parameters when **mode_name** was supplied. |
| 00000155          | AP_MIN_GT_TOTAL | The sum of **min_conwinners_source** and **min_conwinners_target** specifies a number greater than **partner_lu_mode_session_limit**. |
| 00000156          | AP_MODE_CLOSED | The local LU cannot negotiate a nonzero session limit because the local maximum session limit at the partner LU is zero. |
| 00000156          | AP_CNOS_MODE_CLOSED | The local LU cannot negotiate a nonzero session limit because the local maximum session limit at the partner LU is zero. |
| 00000157          | AP_CNOS_MODE_NAME_REJECT | The partner LU does not recognize the specified mode name. |
| 00000159          | AP_RESET_SNA_DRAINS | The SNASVCMG mode does not support the **drain** parameter values. |
| 0000015A          | AP_SINGLE_NOT_SRC_RESP | For a single-session [CNOS](../core/cnos2.md) verb, APPC permits only the local (source) LU to be responsible for deactivating sessions. |
| 0000015B          | AP_BAD_PARTNER_LU_ALIAS | APPC did not recognize the supplied **partner_lu_alias**. |
| 0000015C          | AP_EXCEEDS_MAX_ALLOWED | Your program issued a [CNOS](../core/cnos2.md) verb, specifying a **partner_lu_mode_session_limit** number and **set_negotiable** (NO). |
| 0000015D          | AP_CHANGE_SRC_DRAINS | APPC does not permit **mode_name_select** (ONE) and **drain_source** (YES) when **drain_source** (NO) is currently in effect for the specified mode. |
| 0000015E          | AP_LU_DETACHED |  A command reset the definition of the local LU before the [CNOS](../core/cnos2.md) verb tried to specify the LU. |
| 0000015F          | AP_CNOS_COMMAND_RACE_REJECT | The local LU is currently processing a [CNOS](../core/cnos2.md) verb issued by the partner LU. |
| 00000167          | AP_SNASVCMG_RESET_NOT_ALLOWED  | Your local program attempted to issue the [CNOS](../core/cnos2.md) verbs for the mode named SNASVCMG, specifying a session limit of zero. |
| 000001B4          | AP_DISPLAY_INFO_EXCEEDS_LENGTH  | The returned [DISPLAY](../core/display2.md) information did not fit in the buffer. |
| 000001B5          | DISPLAY_INVALID_CONSTANT  | The value supplied for NUM_SECTIONS or INIT_SEC_LEN is invalid. |
| 00000506          | AP_UNDEFINED_TP_NAME  | In the configuration file for your application, APPC could not find an invokable TP name matching the value of **tp_name**. |
| 00000509          | AP_ALLOCATE_NOT_PENDING  | APPC did not find an incoming allocate (from the invoking TP) to match the value of **tp_name**, supplied by [RECEIVE_ALLOCATE](../core/receive-allocate1.md). **RECEIVE_ALLOCATE** waited for the incoming allocate and eventually timed out. |
| 00000519          | AP_CPSVCMG_MODE_NOT_ALLOWED  | The mode named CPSVCMG cannot be specified as the **mode_name** on the deactivate session verb. |
| 00000525          | AP_INVALID_PROCESS  | The process issuing [RECEIVE_ALLOCATE](../core/receive-allocate1.md) was different from the one started by APPC.  |
| 080F6051          | AP_SECURITY_NOT_VALID  | The user identifier or password specified in the allocation request was not accepted by the partner LU. |
| 084B6031          | AP_TRANS_PGM_NOT_AVAIL_RETRY | The remote LU rejected the allocation request because it was unable to start the requested partner TP. The condition may be temporary, such as a time-out. The reason for the error may be logged on the remote node. Retry the allocation. |
| 084C0000          | AP_TRANS_PGM_NOT_AVAIL_NO_RETRY  | The remote LU rejected the allocation request because it was unable to start the requested partner TP. The condition is permanent. The reason for the error may be logged on the remote node. Do not retry the allocation until the error has been corrected. |
| 10086021          | AP_TP_NAME_NOT_RECOGNIZED  | The partner LU does not recognize the TP name specified in the allocation request. |
| 10086031          | AP_PIP_NOT_ALLOWED  | The allocation request specified PIP data, but either the partner TP does not require this data, or the partner LU does not support it. |
| 10086032          | AP_PIP_NOT_SPECIFIED_CORRECTLY  | The partner TP requires PIP data, but the allocation request specified either no PIP data or an incorrect number of parameters.  |
| 10086034          | AP_CONVERSATION_TYPE_MISMATCH  | The partner LU or TP does not support the conversation type (basic or mapped) specified in the allocation request.   |
| 10086041          | AP_SYNC_LEVEL_NOT_SUPPORTED  | The partner TP does not support the **sync_level** (AP_NONE or AP_CONFIRM_SYNC_LEVEL) specified in the allocation request, or the **sync_level** was not recognized. |
