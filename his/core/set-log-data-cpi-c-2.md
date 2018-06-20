---
title: "Set_Log_Data (CPI-C)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bbd93c60-ee27-473b-b375-89b4a827b6a1
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Set_Log_Data (CPI-C)
The **Set_Log_Data** call (function name **cmsld**) specifies a log message (log data) and its length to be sent to the partner logical unit (LU). This call is allowed only in basic conversations. It overrides the default log data, which is null, and the default log data length, which is zero.  
  
## Syntax  
  
```  
  
CM_ENTRY Set_Log_Data(   
  unsigned char FAR *conversation_ID,    
  unsigned char FAR *log_data,           
  CM_INT32 FAR *log_data_length,         
  CM_INT32 FAR *return_code              
);  
```  
  
#### Parameters  
 *conversation_ID*  
 Supplied parameter. Specifies the identifier for the conversation. The value of this parameter was returned by [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md) or [Accept_Conversation](../core/accept-conversation-cpi-c-2.md).  
  
 *log_data*  
 Supplied parameter. Specifies the starting address of the data to be sent to the partner LU. It can contain up to 512 ASCII characters. The allowed characters are:  
  
- Uppercase and lowercase letters.  
  
- Numerals from 0 through 9.  
  
- Special characters.  
  
- The space.  
  
  *log_data_length*  
  Supplied parameter. Specifies the length of the log data. The range is from 0 through 512 bytes.  
  
  A length of 0 indicates that there is no log data, and the *log_data* parameter is ignored.  
  
  *return_code*  
  The code returned from this call. The valid return codes are listed later in this topic.  
  
## Return Codes  
 CM_OK  
 Primary return code; the call executed successfully.  
  
 CM_PROGRAM_PARAMETER_CHECK  
 Primary return code; one of the following occurred:  
  
- The value specified by *conversation_ID* is invalid.  
  
- The conversation type is set to mapped.  
  
- The value specified by *log_data_length* is out of range (greater than 512 or less than 0).  
  
  CM_PRODUCT_SPECIFIC_ERROR  
  Primary return code; a product-specific error occurred and has been logged in the products error log.  
  
## State Changes  
 The conversation can be in any state except RESET.  
  
 There is no state change.  
  
## Remarks  
 The log data specified by **Set_Log_Data** is sent to the partner LU when the local program issues one of the following calls:  
  
- [Send_Error](../core/send-error-cpi-c-2.md)  
  
- [Deallocate](../core/deallocate-cpi-c-1.md) with the conversations deallocate type set to CM_DEALLOCATE_ABEND  
  
- [Send_Data](../core/send-data-cpi-c-2.md) with the conversations send type set to CM_SEND_AND_DEALLOCATE and the deallocate type set to CM_DEALLOCATE_ABEND  
  
  After sending the log data to the partner LU, the local LU resets the log data to null and the log data length to zero.  
  
  CPI-C automatically converts the log data from ASCII to other encoding standards, such as EBCDIC, as required.