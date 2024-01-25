---
description: "Learn more about: DEACTIVATE_SESSION"
title: "DEACTIVATE_SESSION1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# DEACTIVATE_SESSION
The **DEACTIVATE_SESSION** verb requests Microsoft® Host Integration Server to deactivate a particular session between the local logical unit (LU) and a specified partner LU, or all sessions on a particular mode.  
  
 The following structure describes the verb control block used by the **DEACTIVATE_SESSION** verb.  
  
## Syntax  
  
```  
  
typedef struct deactivate_session {  
    unsigned short  opcode;  
    unsigned char   reserv2[2];  
    unsigned short  primary_rc;  
    unsigned long   secondary_rc;  
    unsigned char   reserv3[8];  
    unsigned char   lu_alias[8];  
    unsigned char   session_id[8];  
    unsigned char   plu_alias[8];  
    unsigned char   mode_name[8];  
    unsigned char   type;  
    unsigned char   reserv4[3];  
    unsigned short  sense_data;  
    unsigned char   fqplu_name[17];  
    unsigned char   reserv5[19];  
} DEACTIVATE_SESSION;   
```  
  
## Members  
 opcode  
 Supplied parameter. Specifies the verb operation code, AP_DEACTIVATE_SESSION.  
  
 reserv2  
 A reserved field.  
  
 primary_rc  
 Returned parameter. Specifies the primary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 secondary_rc  
 Returned parameter. Specifies the secondary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 reserv3  
 A reserved field.  
  
 lu_alias  
 Supplied parameter. Provides the 8-byte ASCII name used locally for the LU.  
  
 session_id  
 Supplied parameter. Provides the 8-byte identifier of the session to deactivate (returned on the **ACTIVATE_SESSION** verb). If this field is set to 8 binary zeros, Host Integration Server deactivates all sessions for the partner LU and mode.  
  
 plu_alias  
 Supplied parameter. Provides the 8-byte ASCII name used locally for the partner LU. If the default remote LU is to be used, fill this parameter with spaces. If the partner LU is to be specified with the **fqplu_name** parameter, fill this parameter with binary zeros.  
  
 mode_name  
 Supplied parameter. Specifies the EBCDIC (type A) mode name.  
  
 type  
 Supplied parameter. Specifies the type of deactivation. Possible values are:  
  
 AP_DEACT_CLEANUP  
 Deactivate the session immediately, without waiting for sessions to end.  
  
 AP_DEACT_NORMAL  
 Do not deactivate the session until all conversations using the session have ended.  
  
 sense_data  
 Returned parameter. Specifies the deactivation sense data for the session.  
  
 reserv4  
 A reserved field.  
  
 fqplu_name  
 Supplied parameter. Provides the partner LU name in EBCDIC (type A) when no **plu_alias** name is defined at the local node and the partner LU is located at a different node. This parameter is ignored if **plu_alias** is specified.  
  
 reserv5  
 A reserved field.  
  
## Return Codes  
 AP_OK  
 Primary return code; the verb executed successfully. The secondary return code indicates the polarity of the established session. The following values can be returned.  
  
 AP_PARAMETER_CHECK  
 Primary return code; the verb did not execute because of a parameter error, specified by one of the following secondary return codes:  
  
 AP_INVALID_LU_ALIAS  
 Secondary return code; APPC cannot find the specified **lu_alias** among those defined.  
  
 AP_INVALID_PLU_ALIAS  
 Secondary return code; APPC did not recognize the specified **plu_alias**.  
  
 AP_INVALID_SESSION_ID  
 Secondary return code; APPC did not recognize the specified **session_id**.  
  
 AP_INVALID_MODE_NAME  
 Secondary return code; APPC did not recognize the specified **mode_name**.  
  
 AP_INVALID_FQPLU_NAME  
 Secondary return code; APPC did not recognize the specified **fqplu_name**.  
  
 AP_INVALID_TYPE  
 Secondary return code; APPC did not recognize the specified **type**.  
  
 AP_COMM_SUBSYSTEM_ABENDED  
 Primary return code; indicates one of the following conditions occurred:  
  
 The node used by this conversation encountered an ABEND.  
  
 The connection between the TP and the PU 2.1 node has been broken (a local area network error occurred).  
  
 The SnaBase at the TP's computer encountered an ABEND.  
  
 The system administrator should examine the error log to determine the reason for the ABEND.  
  
 AP_COMM_SUBSYSTEM_NOT_LOADED  
 Primary return code; a required component could not be loaded or terminated while processing the verb. Thus, communication could not take place. Contact the system administrator for corrective action.  
  
 AP_STACK_TOO_SMALL  
 Primary return code; the stack size of the application is too small to execute the verb. Increase the stack size of your application.  
  
 AP_THREAD_BLOCKING  
 Primary return code; the calling thread is already in a blocking call.
