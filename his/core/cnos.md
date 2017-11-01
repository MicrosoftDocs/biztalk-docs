---
title: "CNOS2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 30627828-544d-444e-bd86-fd38d04f23d9
caps.latest.revision: 3
---
# CNOS
The **CNOS** (Change Number of Sessions) verb establishes APPC LU 6.2 session limits.  
  
 The following structure describes the verb control block used by the **CNOS** verb.  
  
## Syntax  
  
```  
  
typedef struct cnos {  
    unsigned short  opcode;  
    unsigned char   reserv2[2];  
    unsigned short  primary_rc;  
    unsigned long   secondary_rc;  
    unsigned char   key[8];  
    unsigned char   lu_alias[8];  
    unsigned char   plu_alias[8];  
    unsigned char   fqplu_name[17];  
    unsigned char   reserv3;  
    unsigned char   mode_name[8];  
    unsigned int    mode_name_select:1;  
    unsigned int    set_negotiable:1;  
    unsigned int    reserv4:6;  
    unsigned int    reserv5:8;  
    unsigned short  plu_mode_sess_lim;  
    unsigned short  min_conwinners_source;  
    unsigned short  min_conwinners_target;  
    unsigned short  auto_act;  
    unsigned int    drain_target:1;  
    unsigned int    drain_source:1;  
    unsigned int    responsible:1;  
    unsigned int    reserv6:5;  
    unsigned int    reserv7:8;  
} CNOS;   
```  
  
## Members  
 opcode  
 Supplied parameter. Specifies the verb operation code, AP_CNOS.  
  
 reserv2  
 A reserved field.  
  
 primary_rc  
 Returned parameter. Specifies the primary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 secondary_rc  
 Returned parameter. Specifies the secondary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 key  
 Supplied parameter. Specifies either the master or service key in ASCII, if the keylock feature has been secured.  
  
 lu_alias  
 Supplied parameter. Provides the 8-byte ASCII name used locally for the LU.  
  
 plu_alias  
 Supplied parameter. Provides the 8-byte ASCII name used locally for the partner LU.  
  
 fqplu_name  
 Supplied parameter. Provides the partner logical unit (LU) name in EBCDIC (type A) when no **plu_alias** name is defined at the local node and the partner LU is located at a different node.  
  
 mode_name  
 Supplied parameter. Specifies the EBCDIC (type A) mode name to be used when the value of **mode_name_select** is AP_ONE.  
  
 mode_name_select  
 Supplied parameter. Specifies the mode name select for which your program is setting or resetting the session limits and contention-winner polarities. Allowed values are AP_ALL or AP_ONE.  
  
 set_negotiable  
 Supplied parameter. Specifies whether APPC is to change the current setting for the maximum negotiable session limit. Allowed values are AP_YES and AP_NO.  
  
 reserv4  
 A 6-bit reserved field.  
  
 reserv5  
 An 8-bit reserved field.  
  
 plu_mode_sess_lim  
 Supplied parameter. Specifies the session limit when the value for **set_negotiable** is YES. Allowed values are 0 to 32767.  
  
 min_conwinners_source  
 Supplied parameter. Specifies the number of sessions of which the LU is guaranteed to be the contention winner. Allowed values are 0 to 32767.  
  
 min_conwinners_target  
 Supplied parameter. Specifies the minimum number of sessions of which the target LU is guaranteed to be the contention winner. Allowed values are 0 to 32767.  
  
 auto_act  
 Supplied parameter. Specifies the number of the local LUs contention-winner sessions for APPC to activate automatically. Allowed values are 0 to 32767. See the Remarks section of this topic before using this parameter.  
  
 drain_target  
 Supplied parameter. Specifies whether the target LU can drain its waiting (outbound) allocation requests. Allowed values are AP_YES and AP_NO.  
  
 drain_source  
 Supplied parameter. Specifies whether the source LU can drain its waiting (outbound) allocation requests. Allowed values are AP_YES and AP_NO.  
  
 responsible  
 Supplied parameter. Specifies which LU is responsible for deactivating the sessions as a result of resetting the session limit for parallel-session connections. Allowed values are AP_SOURCE and AP_TARGET.  
  
 reserv6  
 A 5-bit reserved field.  
  
 reserv7  
 An 8-bit reserved field.  
  
## Return Codes  
 AP_OK  
 Primary return code; the verb executed successfully.  
  
 AP_CNOS_ACCEPTED  
 Secondary return code; APPC accepts the session limits and responsibility as specified.  
  
 AP_CNOS_NEGOTIATED  
 Secondary return code; APPC accepts the session limits and responsibility as negotiable by the partner LU. Values that can be negotiated are:  
  
 **plu_mode_session_limit**  
  
 **min_conwinners_source**  
  
 **min_conwinners_target**  
  
 **responsible**  
  
 **drain_target**  
  
 AP_ALLOCATION_ERROR  
 Primary return code; APPC has failed to allocate a conversation. The conversation state is set to RESET.  
  
 This code can be returned through a verb issued after [ALLOCATE](../core/allocate.md) or [MC_ALLOCATE](../core/mc-allocate.md).  
  
 AP_ALLOCATION_FAILURE_NO_RETRY  
 Secondary return code; the conversation cannot be allocated because of a permanent condition, such as a configuration error or session protocol error. To determine the error, the system administrator should examine the error log file. Do not retry the allocation until the error has been corrected.  
  
 AP_ALLOCATION_FAILURE_RETRY  
 Secondary return code; the conversation could not be allocated because of a temporary condition, such as a link failure. The reason for the failure is logged in the system error log. Retry the allocation.  
  
 AP_CNOS_LOCAL_RACE_REJECT  
 Primary return code; APPC is currently processing a **CNOS** verb issued by a local LU.  
  
 AP_CNOS_PARTNER_LU_REJECT  
 Primary return code; the partner LU rejected a **CNOS** request from the local LU.  
  
 AP_CNOS_MODE_CLOSED  
 Secondary return code; the local LU cannot negotiate a nonzero session limit because the local maximum session limit at the partner LU is zero.  
  
 AP_CNOS_MODE_NAME_REJECT  
 Secondary return code; the partner LU does not recognize the specified mode name.  
  
 AP_CNOS_COMMAND_RACE_REJECT  
 Secondary return code; the local LU is currently processing a **CNOS** verb issued by the partner LU.  
  
 AP_COMM_SUBSYSTEM_ABENDED  
 Primary return code; indicates one of the following conditions:  
  
 The node used by this conversation encountered an ABEND.  
  
 The connection between the transaction program (TP) and the PU 2.1 node has been broken (a local area network error).  
  
 The SnaBase at the TPs computer encountered an ABEND.  
  
 The system administrator should examine the error log to determine the reason for the ABEND.  
  
 AP_COMM_SUBSYSTEM_NOT_LOADED  
 Primary return code; a required component could not be loaded or terminated while processing the verb. Thus, communication could not take place. Contact the system administrator for corrective action.  
  
 AP_INVALID_KEY  
 Primary return code; the supplied key was incorrect.  
  
 AP_INVALID_VERB_SEGMENT  
 Primary return code; the VCB extended beyond the end of the data segment.  
  
 AP_PARAMETER_CHECK  
 Primary return code; the verb did not execute because of a parameter error.  
  
 AP_ALL_MODE_MUST_RESET  
 Secondary return code; APPC does not permit a nonzero session limit when the **mode_name_select** parameter indicates AP_ALL.  
  
 AP_AUTOACT_EXCEEDS_SESSLIM  
 Secondary return code; on the **CNOS** verb, the value for **auto_act** is greater than the value for **plu_mode_sess_lim**.  
  
 AP_BAD_LU_ALIAS  
 Secondary return code; APPC cannot find the specified **lu_alias** among those defined.  
  
 AP_BAD_PARTNER_LU_ALIAS  
 Secondary return code; APPC did not recognize the supplied **plu_alias**.  
  
 AP_BAD_SNASVCMG_LIMITS  
 Secondary return code; your program specified invalid settings for **plu_mode_sess_lim**, **min_conwinners_source**, or **min_conwinners_target** when **mode_name** was supplied.  
  
 AP_CHANGE_SRC_DRAINS  
 Secondary return code; APPC does not permit **mode_name_select** (ONE) and **drain_source** (YES) when **drain_source** (NO) is currently in effect for the specified mode.  
  
 AP_CNOS_IMPLICIT_PARALLEL  
 Secondary return code; APPC does not permit a program to change the session limit for a mode other than the SNASVCMG mode for the implicit partner template when the template specifies parallel sessions. (The term "template" is used because many of the actual values are yet to be filled in.)  
  
 AP_CPSVCMG_MODE_NOT_ALLOWED  
 Secondary return code; the mode named CPSVCMG cannot be specified as the **mode_name** on the deactivate session verb.  
  
 AP_EXCEEDS_MAX_ALLOWED  
 Secondary return code; your program issued a **CNOS** verb, specifying a **plu_mode_sess_lim** number and **set_negotiable** (AP_NO).  
  
 AP_MIN_GT_TOTAL  
 Secondary return code; the sum of **min_conwinners_source** and **min_conwinners_target** specifies a number greater than **plu_mode_sess_lim**.  
  
 AP_MODE_CLOSED  
 Secondary return code; the local LU cannot negotiate a nonzero session limit because the local maximum session limit at the partner LU is zero.  
  
 AP_RESET_SNA_DRAINS  
 Secondary return code; SNASVCMG does not support the drain parameter values.  
  
 AP_SINGLE_NOT_SRC_RESP  
 Secondary return code; for a single-session **CNOS** verb, APPC permits only the local (source) LU to be responsible for deactivating sessions.  
  
 AP_STACK_TOO_SMALL  
 Primary return code; the stack size of the application is too small to execute the verb. Increase the stack size of your application.  
  
 AP_STATE_CHECK  
 Primary return code; the verb did not execute because it was issued in an invalid state.  
  
 AP_CANT_RAISE_LIMITS  
 Secondary return code; APPC does not permit setting session limits to a nonzero value unless the limits currently are zero.  
  
 AP_LU_DETACHED  
 Secondary return code; a command has reset the definition of the local LU before **CNOS** tried to specify the LU.  
  
 AP_SNASVCMG_RESET_NOT_ALLOWED  
 Secondary return code; your local program attempted to issue the **CNOS** verb for the mode named SNASVCMG, specifying a session limit of zero.  
  
 AP_UNEXPECTED_DOS_ERROR  
 Primary return code; the operating system has returned an error to APPC while processing an APPC verb from the local TP. The operating system return code is returned through the **secondary_rc**. It appears in Intel byte-swapped order. If the problem persists, consult the system administrator.  
  
## Remarks  
 **CNOS** identifies an LU by alias alone. If the same local LU alias is used multiple times in a domain (for backup or other purposes) and that LU alias is specified through **CNOS**, the verb can flow to a different LU than the one intended.  
  
 If CNOS is not issued to set the mode session limit before a program issues its first APPC [ALLOCATE](../core/allocate.md), [MC_ALLOCATE](../core/mc-allocate.md), [SEND_CONVERSATION](../core/send-conversation.md), or [MC_SEND_CONVERSATION](../core/mc-send-conversation.md), or Common Programming Interface for Communications (CPI-C) [Allocate](../core/allocate-cpi-c.md) call for a given partner LU and mode, APPC will internally generate a session limit using the value from the mode definition.  
  
 When setting the limits for a parallel-session connection, the two LUs negotiate the mode session limits, drain settings, and responsibility values. APPC updates these parameters in **CNOS** to reflect the settings agreed to by both LUs during negotiation. Your program can issue [DISPLAY](../core/display.md) to obtain the negotiated values for the mode session limit.  
  
 No **CNOS** negotiation occurs when setting the limits for a single session (that is, the two LUs do not negotiate drain settings or responsibility values). Therefore, coordinate the mode definition parameter settings between partner LUs using a single-session connection by defining a single session mode at each node.  
  
 As part of setting up the initial limits, **CNOS** also sets the guaranteed (that is, the minimum) number of contention-winner and contention-loser sessions and sets the automatic activation count for the source LUs contention-winner sessions. The action of **CNOS** normally affects only the group of sessions with the specified mode name between the source LU and the target LU. Alternatively, one **CNOS** can reset the session limits of all modes for a partner LU.  
  
 APPC enforces the new mode session limit and the contention-winner polarities until one side or the other changes them by issuing a subsequent **CNOS** verb. The **CNOS** transaction is invisible at the target LU's API, regardless of which LU is the target. The results of the **CNOS** transaction can be obtained using **DISPLAY**.