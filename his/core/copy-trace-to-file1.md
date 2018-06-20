---
title: "COPY_TRACE_TO_FILE1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ef9ce29d-7563-4421-ac8a-930b5201f362
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# COPY_TRACE_TO_FILE
The **COPY_TRACE_TO_FILE** verb concatenates individual API/link service trace files to form a single file.  
  
 The following structure describes the verb control block (VCB) used by the **COPY_TRACE_TO_FILE** verb.  
  
## Syntax  
  
```  
  
struct copy_trace_to_file {  
    unsigned short       opcode;  
    unsigned char        opext;  
    unsigned char        reserv2;  
    unsigned short       primary_rc;  
    unsigned long        secondary_rc;  
    unsigned char        reserv3[8];  
    unsigned char        file_name[64];  
    unsigned char        file_option;  
    unsigned char        reserv4[12];  
};   
```  
  
## Remarks  
  
## Members  
 *opcode*  
 Supplied parameter. The verb identifying the operation code, SV_COPY_TRACE_TO_FILE.  
  
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
  
 *file_name*  
 Supplied parameter. Specifies the name of the file to which trace data is to be copied. This parameter is a 64-byte character string, and it can include a path. If the name is fewer than 64 bytes, use spaces to pad it on the right.  
  
 *file_option*  
 Supplied parameter. Specifies the output file copy option:  
  
- Use SV_NEW to copy the trace only if the specified file does not already exist.  
  
- Use SV_OVERWRITE to copy the trace to an existing file, overwriting the current data. The size of the file is increased if necessary; and the file is created if it does not already exist.  
  
  *reserv4*  
  The address at which supplied data resides.  
  
## Return Codes  
 SV_OK  
 Primary return code; the verb executed successfully.  
  
 SV_PARAMETER_CHECK  
 Primary return code; the verb did not execute because of a parameter error.  
  
 SV_INVALID_FILE_OPTION  
  
 Secondary return code; a value other than SV_NEW or SV_OVERWRITE was specified for **file_option**.  
  
 SV_STATE_CHECK  
 Primary return code; the verb did not execute because it was issued in an invalid state.  
  
 SV_COPY_TRACE_IN_PROGRESS  
  
 Secondary return code; a previously issued **COPY_TRACE_TO_FILE** verb is still in progress.  
  
 SV_TRACE_FILE_EMPTY  
  
 Secondary return code; there is no data in the trace files.  
  
 SV_TRACE_NOT_STOPPED  
  
 Secondary return code; a trace was in progress when the verb was issued.  
  
 SV_COMM_SUBSYSTEM_NOT_LOADED  
 Primary return code; a required component could not be loaded or terminated while processing the verb. Thus, communication could not take place. Contact the system administrator for corrective action.  
  
 SV_FILE_ALREADY_EXISTS  
 Primary return code; when the SV_NEW file option was used, the file name specified was the name of an existing file.  
  
 SV_INVALID_VERB  
 Primary return code; the **opcode** parameter did not match the operation code of any verb. No verb executed.  
  
 SV_INVALID_VERB_SEGMENT  
 Primary return code; the VCB extended beyond the end of the data segment.  
  
 SV_OUTPUT_DEVICE_FULL  
 Primary return code; there is insufficient space on the device where the output file resides. Retry the operation after freeing additional disk space.  
  
 SV_UNEXPECTED_DOS_ERROR  
 Primary return code; one of the following conditions occurred:  
  
-   The Microsoft Windows system encountered an error while processing the verb. The operating system return code was returned through the secondary return code. If the problem persists, contact the system administrator for corrective action.  
  
-   A CSV was issued from a message loop that was invoked by another application issuing a Windows **SendMessage** function call, rather than the more common Windows **PostMessage** function call. Verb processing cannot take place.  
  
-   A CSV was issued when **SendMessage** invoked your application. You can determine whether your application has been invoked with **SendMessage** by using the **InSendMessage** Windows API function call.  
  
## Remarks  
 There are two API/link-service trace files. The files are used alternately; tracing switches from one file to the other when one file is full (larger than 250K). When **COPY_TRACE_TO_FILE** is called, these trace files are concatenated and copied to a single file, the name of which is specified as a parameter to the call.  
  
 API/link-service tracing is stopped before issuing the verb, and restarted after the copy is complete. The trace files are reset when this verb is successfully completed.