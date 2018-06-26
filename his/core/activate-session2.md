---
title: "ACTIVATE_SESSION2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c8836ba-06cd-4f8e-a1df-dfb8f2adf927
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# ACTIVATE_SESSION
The **ACTIVATE_SESSION** verb requests Microsoft® Host Integration Server to activate a session between the local logical unit (LU) and a specified partner LU, using a specified mode. This verb completes either when the specified session has become active or when it has failed.  
  
 The following structure describes the verb control block used by the **ACTIVATE_SESSION** verb.  
  
## Syntax  
  
```  
  
typedef struct activate_session {  
    unsigned short  opcode;  
    unsigned char   reserv2[2];  
    unsigned short  primary_rc;  
    unsigned long   secondary_rc;  
    unsigned char   reserv3[8];  
    unsigned char   lu_alias[8];  
    unsigned char   plu_alias[8];  
    unsigned char   mode_name[8];  
    unsigned char   fqplu_name[17];  
    unsigned char   polarity;  
    unsigned char   session_id[8];  
    unsigned long   conv_group_id;  
    unsigned char   reserv4[1];  
    unsigned char   type;  
    HANDLE          deactivation_event;  
    unsigned short* p_deactivation_status;  
    unsigned char   reserv5[10];  
} ACTIVATE_SESSION;   
```  
  
## Members  
 opcode  
 Supplied parameter. Specifies the verb operation code, AP_ACTIVATE_SESSION.  
  
 reserv2  
 A reserved field.  
  
 primary_rc  
 Returned parameter. Specifies the primary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 secondary_rc  
 Returned parameter. Specifies the secondary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 reserv3  
 A reserved field.  
  
 lu_alias  
 Supplied parameter. Provides the 8-byte ASCII name used locally for the LU. If the default local LU is to be used, fill this parameter with spaces.  
  
 plu_alias  
 Supplied parameter. Provides the 8-byte ASCII name used locally for the partner LU. If the default remote LU is to be used, fill this parameter with spaces. If the partner LU is to be specified with the **fqplu_name** parameter, fill this parameter with binary zeros.  
  
 mode_name  
 Supplied parameter. Specifies the EBCDIC (type A) mode name.  
  
 fqplu_name  
 Supplied parameter. Provides the partner LU name in EBCDIC (type A) when no **plu_alias** name is defined at the local node and the partner LU is located at a different node. This parameter is ignored if **plu_alias** is specified.  
  
 polarity  
 Supplied parameter. Specifies the polarity for the session. The possible values are:  
  
 AP_POL_EITHER  
 If AP_POL_EITHER is set, ACTIVATE_SESSION activates a first speaker session if available; otherwise a bidder session is activated.  
  
 AP_POL_FIRST_SPEAKER  
 If AP_POL_FIRST_SPEAKER is set, ACTIVATE_SESSION only succeeds if a session of the requested polarity is available.  
  
 AP_POL_BIDDER  
 If AP_POL_BIDDER is set, ACTIVATE_SESSION only succeeds if a session of the requested polarity is available.  
  
 session_id  
 Returned parameter. Provides the 8-byte identifier of the activate session.  
  
 conv_group_id  
 Returned parameter. Provides the conversation group identifier. This parameter can be specified on **ALLOCATE** and **MC_ALLOCATE** verbs to start conversations on this particular session.  
  
 reserv4  
 A reserved field.  
  
 type  
 Supplied parameter. Specifies the type of activation. Possible values are:  
  
 AP_ACT_ACTIVE  
 If AP_ACT_ACTIVE is specified, then Host Integration Server will attempt to start the required session (by sending the BIND or INIT-SELF).  
  
 AP_ACT_PASSIVE  
 If AP_ACT_PASSIVE is specified, then Host Integration Server will not attempt to start the session and the verb will complete when the partner has started the session.  
  
 deactivation_event  
 Supplied parameter. Provides an event handle that APPC is to signal when the session is deactivated. The event handle should be obtained by calling either the **CreateEvent** or **OpenEvent** Win32® function.  
  
 p_deactivation_status  
 Returned parameter. A pointer to a value that is set when the deactivation event is signaled to provide completion status. The following values can be returned.  
  
 AP_SESSION_DEACTIVATED  
  AP_COMM_SUBSYSTEM_ABENDED  
  reserv5  
 A reserved field.  
  
## Return Codes  
 AP_OK  
 Primary return code; the verb executed successfully. The secondary return code indicates the polarity of the established session. The following values can be returned.  
  
 AP_POL_FIRST_SPEAKER  
  AP_POL_BIDDER  
  AP_PARAMETER_CHECK  
 Primary return code; the verb did not execute because of a parameter error.  
  
 AP_INVALID_LU_ALIAS  
 Secondary return code; APPC cannot find the specified **lu_alias** among those defined.  
  
 AP_INVALID_PLU_ALIAS  
 Secondary return code; APPC did not recognize the specified **plu_alias**.  
  
 AP_INVALID_MODE_NAME  
 Secondary return code; APPC did not recognize the specified **mode_name**.  
  
 AP_INVALID_FQPLU_NAME  
 Secondary return code; APPC did not recognize the specified **fqplu_name**.  
  
 AP_INVALID_POLARITY  
 Secondary return code; APPC did not recognize the specified **polarity**.  
  
 AP_INVALID_TYPE  
 Secondary return code; APPC did not recognize the specified **type**.  
  
 AP_ACTIVATION_FAIL_NO_RETRY  
 Primary return code; the session could not be activated because of a condition that requires action (such as a configuration mismatch or a session protocol error).  
  
 AP_ACTIVATION_FAIL_RETRY  
 Primary return code; the session could not be activated because of a temporary condition (such as a link failure).  
  
 AP_SESSION_LIMITS_EXCEEDED  
 Primary return code; the session could not be activated because the session limits have been exceeded.  
  
 AP_SESSION_LIMITS_CLOSED  
 Primary return code; the session could not be activated because the session limits are closed (that is, zero).  
  
 AP_COMM_SUBSYSTEM_ABENDED  
 Primary return code; indicates one of the following conditions occurred:  
  
 The node used by this conversation encountered an ABEND.  
  
 The connection between the TP and the PU 2.1 node has been broken (local area network error occurred).  
  
 The SnaBase at the TP's computer encountered an ABEND.  
  
 The system administrator should examine the error log to determine the reason for the ABEND.  
  
 AP_COMM_SUBSYSTEM_NOT_LOADED  
 Primary return code; a required component could not be loaded or terminated while processing the verb. Thus, communication could not take place. Contact the system administrator for corrective action.  
  
 AP_STACK_TOO_SMALL  
 Primary return code; the stack size of the application is too small to execute the verb. Increase the stack size of your application.  
  
 AP_THREAD_BLOCKING  
 Primary return code; the calling thread is already in a blocking call.  
  
## Remarks  
 This verb supports both active and passive activation.  
  
 The active form of this verb results in Host Integration Server trying to initiate the session (by sending a BIND for independent LUs or an INIT-SELF for dependent LUs). The active form of this verb will also result in the following behavior:  
  
- If the connection to the partner LU is inactive and is configured as on-demand, the Node will attempt to start the connection.  
  
- If dynamic partnering is being used, the Node will set up the LU-LU/MODE partnership.  
  
- If CNOS has not run, the Node will start CNOS (but will not change any of the session limits).  
  
  The passive form does not attempt to start the session, but completes when the LU is started by a BIND from its partner LU. For independent LUs, multiple passive **ACTIVATE_SESSION** verbs can be queued up for the same LU-LU/MODE, and complete in turn as new sessions are started.  
  
  This verb also includes a deactivation event, which is posted when the session is deactivated by any method other than a **DEACTIVATE_SESSION** verb (for example, an unsolicited UNBIND from its partner LU results in this event being posted).