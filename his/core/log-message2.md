---
title: "LOG_MESSAGE2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9011731a-8ec6-42b1-8f1a-e7dbd6985e50
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# LOG_MESSAGE
For OS/2 only, the **LOG_MESSAGE** verb records a message in the error log file and optionally displays the message on the users screen. This verb is included for compatibility with existing applications.  
  
 The following structure describes the verb control block (VCB) used by the **LOG_MESSAGE** verb.  
  
## Syntax  
  
```  
  
struct log_message {  
    unsigned short       opcode;  
    unsigned char        opext;  
    unsigned char        reserv2;  
    unsigned short       primary_rc;  
    unsigned long        secondary_rc;  
    unsigned short       msg_num;  
    unsigned char        origntr_id[8];  
    unsigned char        msg_file_name[3];  
    unsigned char        msg_act;  
    unsigned short       msg_ins_len;  
    unsigned char FAR *  msg_ins_ptr;  
};  
```  
  
## Remarks  
  
## Members  
 *opcode*  
 Supplied parameter. The verb identifying the operation code, SV_LOG_MESSAGE.  
  
 *opext*  
 A reserved field.  
  
 *reserv2*  
 A reserved field.  
  
 *primary_rc*  
 Returned parameter. Specifies the primary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 *secondary_rc*  
 Returned parameter. Specifies the secondary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 *msg_num*  
 Supplied parameter. Specifies the number of the message in the message file specified by **msg_file_name**.  
  
 *origntr_id*  
 Supplied parameter. Specifies the name of the component issuing **LOG_MESSAGE** or an 8-byte, user-supplied string.  
  
 *msg_file_name*  
 Supplied parameter. Specifies the name of the file containing the message to be logged.  
  
 *msg_act*  
 Supplied parameter. Specifies the action to be taken when processing the message:  
  
- Use SV_INTRV to log the intervention with a severity level of 12 and display the message on the users screen. The user must press a key to remove the message from the screen.  
  
- Use SV_NO_INTRV to log the intervention with a severity level of 12 but not display the message.  
  
  *msg_ins_len*  
  Supplied parameter. Specifies the length of data to be inserted into the message. Set this parameter to zero if no data is to be inserted.  
  
  msg_ins_ptr  
  Supplied parameter. Specifies the address of the data to be inserted into the message.  
  
  Use this parameter only if **msg_ins_len** is greater than zero.  
  
## Return Codes  
 SV_OK  
 Primary return code; the verb executed successfully.  
  
 SV_PARAMETER_CHECK  
 Primary return code; the verb did not execute because of a parameter error.  
  
 SV_INVALID_DATA_SEGMENT  
  
 Secondary return code; the data that was to be inserted into the message extended beyond the segment boundary.  
  
 SV_INVALID_MESSAGE_ACTION  
  
 Secondary return code; the **msg_act** parameter contained an invalid value.  
  
 SV_COMM_SUBSYSTEM_NOT_LOADED  
 Primary return code; a required component could not be loaded or terminated while processing the verb. Thus, communication could not take place. Contact the system administrator for corrective action.  
  
 SV_INVALID_VERB  
 Primary return code; the **opcode** parameter did not match the operation code of any verb. No verb executed.  
  
 SV_INVALID_VERB_SEGMENT  
 Primary return code; the VCB extended beyond the end of the data segment.  
  
 SV_UNEXPECTED_DOS_ERROR  
 Primary return code; one of the following conditions occurred:  
  
-   The Microsoft Windows system encountered an error while processing the verb. The operating system return code was returned through the secondary return code. If the problem persists, contact the system administrator for corrective action.  
  
-   A CSV was issued from a message loop that was invoked by another application issuing a Windows **SendMessage** function call, rather than the more common Windows **PostMessage** function call. Verb processing cannot take place.  
  
-   A CSV was issued when **SendMessage** invoked your application. You can determine whether your application has been invoked with **SendMessage** by using the **InSendMessage** Windows API function call.  
  
## Remarks  
 The value for **msg_file_name** must be three characters long. Pad with spaces if necessary. The .MSG extension is added automatically.  
  
 The total length of **msg_ins_len**, including header information (40 bytes), message text, and inserted data, should not exceed 256 bytes. If the length is greater than 256 bytes, the communication system will attempt to log only the header information and inserted text; the message text will be left out.  
  
 When you create the log message file, you can specify where in the message the additional data is to be inserted. Further information is provided below.  
  
 The data for **msg_ins_ptr** consists of a series of up to nine null-terminated strings. (Because IBM OS/2 ES version 1.0 supports only three data strings, you may want to limit the inserted text to three strings to ensure compatibility.)  
  
## Creating a Message File  
 If you want to create your own message file, you must use the utility MKMSGF.  
  
 The first three characters of the message number must match the three-character name of the log message file. These three characters are declared at the top of the file as well.  
  
 The system finds the message file as follows:  
  
-   If you use your own message file, the system assumes the file is in the same directory as your programs executable file.  
  
-   If you use the default message file, COM.MSG, the system finds the file automatically, provided the SnaBase for Microsoft Host Integration Server is loaded.  
  
-   If you use the default message file without loading the previously-mentioned software, the system expects DPATH to indicate the path to the message file. This applies only to the Windows version 3.*x* and OS/2 operating systems.