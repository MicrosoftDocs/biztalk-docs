---
title: "DEFINE_TRACE1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f23202bc-d2e7-4ca5-8f75-aefdf0bec3a0
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# DEFINE_TRACE
The **DEFINE_TRACE** verb enables or disables tracing for specified APIs and controls the amount of tracing.  
  
 The following structure describes the verb control block (VCB) used by the **DEFINE_TRACE** verb.  
  
## Syntax  
  
```  
  
struct define_trace {  
    unsigned short       opcode;  
    unsigned char        opext;  
    unsigned char        reserv2;  
    unsigned short       primary_rc;  
    unsigned long        secondary_rc;  
    unsigned char        reserv3[8];  
    unsigned char        dt_set;  
    unsigned char        appc;  
    unsigned char        reserv4;  
    unsigned char        srpi;  
    unsigned char        sdlc;  
    unsigned char        tkn_rng_dlc;  
    unsigned char        pcnet_dlc;  
    unsigned char        dft;  
    unsigned char        acdi;  
    unsigned char        reserv5;  
    unsigned char        ehllapi;  
    unsigned char        x25_api;  
    unsigned char        x25_dlc;  
    unsigned char        twinax;  
    unsigned char        reserv6;  
    unsigned char        lua_api;  
    unsigned char        etherand;  
    unsigned char        subsym;  
    unsigned char        reserv7[8];  
    unsigned char        reset_trc;  
    unsigned short       trunc;  
    unsigned short       strg_size;  
    unsigned char        reserv8;  
    unsigned char        phys_link[8];  
    unsigned char        reserv9[56];  
};   
```  
  
## Remarks  
  
## Members  
 *opcode*  
 Supplied parameter. The verb identifying the operation code, SV_DEFINE_TRACE.  
  
 *opext*  
 A reserved field.  
  
 *reserv2*  
 A reserved field.  
  
 *primary_rc*  
 Returned parameter. Specifies the primary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 *secondary_rc*  
 Returned parameter. Specifies the secondary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 *reserv3*  
 A reserved field.  
  
 *dt_set*  
 Supplied parameter. Sets the trace state.  
  
- Use SV_ON to enable tracing for a particular API if the parameter pertaining to the API (such as **appc** or **comm_serv**) is set to SV_CHANGE.  
  
- Use SV_OFF to disable tracing for a particular API if the parameter pertaining to the API is set to SV_CHANGE.  
  
  *appc*  
  Supplied parameter. Indicates whether tracing of APPC is desired.  
  
- Use SV_CHANGE to enable or disable tracing for APPC, depending on the **dt_set** parameter.  
  
- Use SV_IGNORE to leave tracing in its current state for APPC.  
  
  The allowed values turn bit 0 on or off; bits 1 through 7 are reserved.  
  
  *reserv4*  
  A reserved field.  
  
  *srpi*  
  Supplied parameter. Indicates whether tracing of SRPI is desired.  
  
- Use SV_CHANGE to enable or disable tracing for APPC, depending on the **dt_set** parameter.  
  
- Use SV_IGNORE to leave tracing in its current state for APPC.  
  
  *sdlc*  
  A reserved field.  
  
  *tkn_rng_dlc*  
  A reserved field.  
  
  *pcnet_dlc*  
  A reserved field.  
  
  *dft*  
  A reserved field.  
  
  *acdi*  
  A reserved field.  
  
  *reserv5*  
  A reserved field.  
  
  *comm_serv*  
  Supplied parameter. Indicates whether tracing of COMM_SERV_API is desired.  
  
- Use SV_CHANGE to enable or disable tracing for APPC, depending on the **dt_set** parameter.  
  
- Use SV_IGNORE to leave tracing in its current state for APPC.  
  
  *ehllapi*  
  A reserved field.  
  
  *x25_api*  
  A reserved field.  
  
  *x25_dlc*  
  A reserved field.  
  
  *twinax*  
  A reserved field.  
  
  reserv6  
  A reserved field.  
  
  *lua_api*  
  A reserved field.  
  
  *etherand*  
  A reserved field.  
  
  *subsym*  
  A reserved field.  
  
  *reserv7*  
  A reserved field.  
  
  *reset_trc*  
  Supplied parameter. Indicates whether the trace file pointer should be reset.  
  
- Use SV_NO to not reset the trace file pointer to the start of the trace file. Previous trace records are not overwritten.  
  
- Use SV_YES to reset the trace file pointer to the start of the trace file. Previous trace records are overwritten.  
  
  *trunc*  
  Supplied parameter. Specifies the maximum number of bytes for each trace record. Excess bytes are truncated. Set this value to zero if you do not want truncation.  
  
  *strg_size*  
  A reserved field.  
  
  *reserv8*  
  A reserved field.  
  
  *phys_link*  
  A reserved field.  
  
  *reserv9*  
  A reserved field.  
  
## Return Codes  
 SV_OK  
 Primary return code; the verb executed successfully.  
  
 SV_PARAMETER_CHECK  
 Primary return code; the verb did not execute because of a parameter error.  
  
 SV_INVALID_RESET_TRACE  
  
 Secondary return code; the **reset_trc** parameter contained an invalid value.  
  
 SV_INVALID_SET  
  
 Secondary return code; the **dt_set** parameter contained an invalid value.  
  
 SV_STATE_CHECK  
 Primary return code; the verb did not execute because it was issued in an invalid state.  
  
 SV_COPY_TRACE_IN_PROGRESS  
  
 Secondary return code; a previously issued [COPY_TRACE_TO_FILE](../core/copy-trace-to-file1.md) is still in progress. Traces cannot be active while using **DEFINE_TRACE**.  
  
 SV_COMM_SUBSYSTEM_NOT_LOADED  
 Primary return code; a required component could not be loaded or terminated while processing the verb. Thus, communication could not take place. Contact the system administrator for corrective action.  
  
 SV_INVALID_VERB  
 Primary return code; the **opcode** parameter did not match the operation code of any verb. No verb executed.  
  
 SV_INVALID_VERB_SEGMENT  
 Primary return code; the VCB extended beyond the end of the data segment.  
  
 SV_UNEXPECTED_DOS_ERROR  
 Primary return code; one of the following conditions occurred:  
  
-   The Microsoft® Windows® system encountered an error while processing the verb. The operating system return code was returned through the secondary return code. If the problem persists, contact the system administrator for corrective action.  
  
-   A CSV was issued from a message loop that was invoked by another application issuing a Windows **SendMessage** function call, rather than the more common Windows **PostMessage** function call. Verb processing cannot take place.  
  
-   A CSV was issued when **SendMessage** invoked your application. You can determine whether your application has been invoked with **SendMessage** by using the **InSendMessage** Windows API function call.  
  
## Remarks  
 For information on how to run and use traces, see the appropriate manual for your product.