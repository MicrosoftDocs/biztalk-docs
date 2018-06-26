---
title: "Set_Fill (CPI-C)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a87b0634-3469-437f-acf5-758d9abd192f
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Set_Fill (CPI-C)
The **Set_Fill** call (function name **cmsf**) specifies whether programs will receive data in the form of logical records or as a specified length of data. This call is allowed only in basic conversations.  
  
## Syntax  
  
```  
  
CM_ENTRY Set_Fill(   
  unsigned char FAR *conversation_ID,    
  CM_INT32 FAR *fill,                    
  CM_INT32 FAR *return_code              
);  
```  
  
#### Parameters  
 *conversation_ID*  
 Supplied parameter. Specifies the identifier for the conversation. The value of this parameter was returned by [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md) or [Accept_Conversation](../core/accept-conversation-cpi-c-2.md).  
  
 *fill*  
 Supplied parameter. Specifies the form in which programs will receive data. The following are possible choices:  
  
 CM_FILL_BUFFER  
 The local program receives data until the number of bytes specified by the *requested_length* parameter of the **Receive** call is reached or until the end of the data. Data is received without regard for the logical-record format.  
  
 CM_FILL_LL  
 Data is received in logical-record format. The data received can be a complete logical record, a portion of a logical record equal to the *requested_length* parameter of the [Receive](../core/receive-cpi-c-2.md) call, or the end of a logical record.  
  
 *return_code*  
 The code returned from this call. The valid return codes are listed later in this topic.  
  
## Return Codes  
 CM_OK  
 Primary return code; the call executed successfully.  
  
 CM_PROGRAM_PARAMETER_CHECK  
 Primary return code; one of the following occurred:  
  
- The value specified by *conversation_ID* or *fill* is invalid.  
  
- The current conversation is mapped.  
  
  CM_PRODUCT_SPECIFIC_ERROR  
  Primary return code; a product-specific error occurred and has been logged in the products error log.  
  
## State Changes  
 The conversation can be in any state except RESET.  
  
 There is no state change.  
  
## Remarks  
 **Set_Fill** overrides the default *fill* established by [Initialize_Conversation](../core/initialize-conversation-cpi-c-1.md) or [Accept_Conversation](../core/accept-conversation-cpi-c-2.md). The default *fill* is CM_FILL_LL.  
  
 The *fill* value affects all subsequent [Receive](../core/receive-cpi-c-2.md) calls. It can be changed by reissuing the **Set_Fill** call.