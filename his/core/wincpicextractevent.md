---
title: "WinCPICExtractEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 60217d70-b12c-4d3c-afc8-63ea92b7b63d
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# WinCPICExtractEvent
The **WinCPICExtractEvent** function provides a method for an application to determine the event handle being used for a Microsoft® Windows® Common Programming Interface for Communications (CPI-C) conversation.  
  
## Syntax  
  
```  
  
        VOID WINAPI WinCPICExtractEvent(   
unsigned char FAR*conversation_ID,HANDLE FAR*event_handle,    CM_INT32 FAR*return_code);  
```  
  
#### Parameters  
 *conversation_ID*  
 Specifies the identifier for the conversation for which this event is used. This parameter is returned by the initial [Accept_Conversation](../core/accept-conversation-cpi-c.md) call.  
  
 *event_handle*  
 Returned parameter. The handle of the event being used by this conversation. If no handle has been registered, this parameter returns as a NULL.  
  
 *return_code*  
 The code returned from this call. The valid return codes are listed later in this topic.  
  
## Return Codes  
 CM_OK  
 The function executed successfully.  
  
 CM_PROGRAM_PARAMETER_CHECK  
 One or more of the parameters passed to this function are invalid.  
  
## Remarks  
 When a verb is issued on a nonblocking conversation, it returns CM_OPERATION_INCOMPLETE if it is going to complete asynchronously. If an event has been registered with the conversation, the application can call **WaitForSingleObject** or **WaitForMultipleObjects** to be notified of the completion of the verb. **WinCPICExtractEvent** allows a CPI-C applicationto determine this event handle. When the verb has completed, the application must call [Wait_For_Conversation](../core/wait-for-conversation-cpi-c.md)to determine the return code for the asynchronous verb. The [Cancel_Conversation](../core/cancel-conversation-cpi-c.md)function can be called to cancel an operation and conversation.  
  
 If no event has been registered, the asynchronous verb completes as it does at present, which is by posting a message to the window that the application has registered with the CPI-C library.