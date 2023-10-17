---
description: "Learn more about: RECEIVE_LOG_DATA"
title: "RECEIVE_LOG_DATA2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 61bebfd0-a6a9-4c68-87c3-09665fc90448
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# RECEIVE_LOG_DATA
The **RECEIVE_LOG_DATA** verb allows the user to register to receive the log data associated with an inbound Function Management Header 7 (FMH7) error report. The verb passes a buffer to APPC, and any log data received is placed in that buffer. APPC continues to use this buffer as successive FMH7s arrive until it is provided with another one (that is, until the transaction program (TP) issues another **RECEIVE_LOG_DATA** specifying a different buffer or no buffer at all).  
  
 Note that the TP itself is responsible for allocating and freeing the buffer. After the buffer has been passed to APPC, the TP should either issue another **RECEIVE_LOG_DATA** specifying a new buffer or a zero-length buffer, or wait until the conversation has finished before freeing the original buffer.  
  
 When an FMH7 is received, APPC copies any associated error log general data stream (GDS) into the buffer. If there is no associated error log variable, the buffer is zeroed out. It is up to the TP to check the buffer whenever a return code from a receive verb indicates that an error has been received.  
  
 The following structure describes the verb control block (VCB) used by the **RECEIVE_LOG_DATA** verb.  
  
## Syntax  
  
```  
  
struct receive_log_data {  
    unsigned short      opcode;  
    unsigned char       opext;  
    unsigned char       reserv1;  
    unsigned short      primary_rc;  
    unsigned long       secondary_rc;  
    unsigned char       tp_id[8];  
    unsigned long       conv_id;  
    unsigned short      log_dlen;  
    unsigned char FAR * log_dptr;  
};   
```  
  
## Members  
 *opcode*  
 Supplied parameter. Specifies the verb operation code, AP_B_RECEIVE_LOG_DATA.  
  
 *opext*  
 Supplied parameter. Specifies the verb operation extension, AP_BASIC_CONVERSATION.  
  
 *reserv1*  
 A reserved field.  
  
 *primary_rc*  
 Returned parameter. Specifies the primary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 *secondary_rc*  
 Returned parameter. Specifies the secondary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 *tp_id*  
 Supplied parameter. Identifies the local TP. The value of this parameter is returned by [TP_STARTED](../core/tp-started2.md) in the invoking TP or by [RECEIVE_ALLOCATE](../core/receive-allocate1.md) in the invoked TP.  
  
 *conv_id*  
 Supplied parameter. Provides the conversation identifier. The value of this parameter is returned by [ALLOCATE](../core/allocate2.md) in the invoking TP or by **RECEIVE_ALLOCATE** in the invoked TP.  
  
 *log_dlen*  
 Supplied parameter. Specifies the maximum length of log data that APPC can place in the buffer (that is, the buffer size). The range is from 0 through 65535. Note that a length of zero here indicates that any previous **RECEIVE_LOG_DATA** verb should be canceled.  
  
 *log_dptr*  
 Supplied parameter. Specifies the address of the buffer that APPC will use to store the log data.  
  
## Return Codes  
 AP_OK  
 Primary return code; the verb executed successfully.  
  
 AP_PARAMETER_CHECK  
 Primary return code; the verb did not execute because of a parameter error.  
  
 AP_BAD_CONV_ID  
  
 Secondary return code; the value of **conv_id** did not match a conversation identifier assigned by APPC.  
  
 AP_BAD_TP_ID  
  
 Secondary return code; the value of **tp_id** did not match a TP identifier assigned by APPC.
