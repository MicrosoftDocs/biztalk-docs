---
description: "Learn more about: Receiving Data"
title: "Receiving Data1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6aa05d6d-c0a7-400a-9c6d-846c7c23e230
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Receiving Data
The following calls or extensions enable a program to receive data from its partner program:  
  
> [!NOTE]
>  The names of the calls are pseudonyms. The actual C function names appear in parentheses after the pseudonyms. For example, **Accept_Conversation** is the pseudonym for a call. The actual function name is **cmaccp**.  
  
 [Receive](./receive-cpi-c-2.md)( **cmrcv**)  
 Issuing this call while the conversation is in RECEIVE state causes the local program to receive any data that is currently available from the partner program. If no data is available and the receive type is set to CM_RECEIVE _AND_WAIT, the local program waits for data to arrive. If the receive type is set to CM_RECEIVE_IMMEDIATE, the program does not wait.  
  
 Issuing this call while the conversation is in SEND or SEND_PENDING state is allowed only if the receive type is set to CM_RECEIVE_AND_WAIT. This flushes the logical unit's (LU) send buffer and changes the conversation state to RECEIVE. The local program then begins to receive data.  
  
 [Set_Fill](./set-fill-cpi-c-1.md)( **cmsf**)  
 Used in a basic conversation, this call sets the conversation's fill type, which specifies whether programs will receive data in the form of logical records or as a specified length of data. This call has an effect only in basic conversations. The fill value affects all subsequent **Receive** calls. It can be changed by reissuing **Set_Fill**.  
  
 [Set_Processing_Mode](./set-processing-mode-cpi-c-2.md)( **cmspm**)  
 Specifies for the conversation whether subsequent calls will be returned when the operation they have requested is complete (blocking) or immediately after the operation is initiated (non-blocking). A program is notified of the completion of non-blocking calls when it issues [Wait_For_Conversation](./wait-for-conversation-cpi-c-1.md) or through a Microsoft Windows message sent to a WndProc identified by the *hwndNotify* parameter in **Specify_Windows_Handle**.  
  
 [Set_Receive_Type](./set-receive-type-cpi-c-2.md)( **cmsrt**)  
 Sets the conversation's receive type, which specifies whether a program issuing a **Receive** call will wait for data to arrive if data is not available. The receive type value affects all subsequent **Receive** calls. It can be changed by reissuing **Set_Receive_Type**.  
  
 [Specify_Windows_Handle](./specify-windows-handle-cpi-c-2.md)( **xchwnd**)  
 Sets the window handle to which a message is sent on completion of an operation in non-blocking mode. An application can set the processing mode by calling **Set_Processing_Mode**. If the window handle is set to NULL or this call is never issued, then the application must call **Wait_For_Conversation** to be notified when the outstanding operation completes.
