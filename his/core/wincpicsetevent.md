---
title: "WinCPICSetEvent1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c5a0b5eb-2534-42c8-8b6e-c1042c9aeb39
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# WinCPICSetEvent
The **WinCPICSetEvent** function associates an event handle with a verb completion.  
  
## Syntax  
  
```  
  
        VOID WINAPI WinCPICSetEvent(   
unsigned char FAR* conversation_ID,HANDLE FAR* event_handle,  
CM_INT32 FAR*return_code);  
```  
  
#### Parameters  
 *conversation_ID*  
 Specifies the identifier for the conversation for which this event is used. This parameter is returned by the initial [Accept_Conversation](../core/accept-conversation-cpi-c.md) call.  
  
 *event_handle*  
 The handle of the event that is to be cleared when an asynchronous verb on the conversation completes. This parameter can replace an already defined event or remove an already defined event (by having NULL as the parameter).  
  
 *return_code*  
 The code returned from this call. The valid return codes are listed later in this topic.  
  
## Return Codes  
 CM_OK  
 The function executed successfully.  
  
 CM_PROGRAM_PARAMETER_CHECK  
 One or more of the parameters passed to this function are invalid.  
  
 CM_OPERATION_NOT_ACCEPTED  
 This value indicates that a previous operation on this conversation is incomplete and the **WinCPICSetEvent** call was not accepted.  
  
## Remarks  
 When a verb is issued on a nonblocking conversation, it returns CM_OPERATION_INCOMPLETE if it is going to complete asynchronously. If an event has been registered with the conversation, the application can call **WaitForSingleObject** or **WaitForMultipleObjects** to be notified of the completion of the verb. When the verb has completed, the application must call [Wait_For_Conversation](../core/wait-for-conversation-cpi-c.md)to determine the return code for the asynchronous verb.  
  
 It is the responsibility of the application to reset the event, as it is with other APIs.  
  
## See Also  
 [Cancel_Conversation (CPI-C)](../core/cancel-conversation-cpi-c.md)