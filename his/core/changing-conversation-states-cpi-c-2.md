---
title: "Changing Conversation States (CPI-C)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d91c93ea-24c6-482d-b6c0-0d9d00e48c27
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Changing Conversation States (CPI-C)
A change in the conversation state can result from:  
  
- A call made by the local transaction program (TP).  
  
- A call made by the partner TP.  
  
- An error condition.  
  
  The following example shows how Common Programming Interface for Communications (CPI-C) calls can change the state of the conversation from SEND to RECEIVE and from RECEIVE to SEND.  
  
> [!NOTE]
>  Any TP can send or receive data, regardless of whether it is the invoking TP (the TP that started the conversation) or the invokable TP (the TP that responded to a request to start a conversation).  
  
 This example shows how CPI-C calls can change the conversation state. In this table, each conversation state appears in bold and precedes the CPI-C calls that are used while in that state.  
  
|Issued by the invoking TP|Issued by the invokable TP|  
|-------------------------------|--------------------------------|  
|**Conversation state: RESET**||  
|Initialize_Conversation||  
|**Conversation state: INITIALIZE**||  
|Set_Sync_Level||  
|(sync_level=CM_CONFIRM)||  
|Allocate||  
|**Conversation state: SEND**||  
|Send_Data||  
|Prepare_to_Receive|**Conversation state: RESET**|  
||Accept_Conversation|  
||**Conversation state: RECEIVE**|  
||(status_received=     CM_CONFIRM_SEND_RECEIVED)|  
||**Conversation state: CONFIRM_SEND**|  
||Confirm|  
||**Conversation state: SEND**|  
|(return_code=CM_OK)|Send_Data|  
|**Conversation state: RECEIVE**|Confirm|  
|(status_received=    CM_CONFIRM_RECEIVED)||  
|**Conversation state: CONFIRM**||  
|Request_To_Send||  
|Confirmed||  
|**Conversation state: RECEIVE**|(return_code=CM_OK)|  
||(request_to_send_received=    CM_REQ_TO_SEND_RECEIVED)|  
||Prepare_To_Receive|  
|Receive||  
|(status_received=     CM_CONFIRM_SEND_RECEIVED)||  
|**Conversation state: CONFIRM_SEND**||  
|Confirmed||  
|**Conversation state: SEND**|(return_code=CM_OK)|  
||**Conversation state: RECEIVE**|  
|Send_Data||  
|Deallocate||  
||Receive|  
||(status_received=    CM_CONFIRM_DEALLOC_RECEIVED)|  
||**Conversation state:** <br />**CONFIRM_DEALLOCATE**|  
||Confirmed|  
|(return_code=CM_OK)|**Conversation state: RESET**|  
|**Conversation state: RESET**||  
  
## Initial States  
 Before the conversation is allocated, the state is RESET for both TPs.  
  
 In the example, after the conversation is allocated, the initial state is SEND for the invoking TP and RECEIVE for the invokable TP.  
  
## Changing to RECEIVE State  
 The [Prepare_To_Receive](./prepare-to-receive-cpi-c-1.md) call allows a TP to change the conversation from SEND to RECEIVE state. This call:  
  
-   Flushes the local LU's send buffer.  
  
-   Sends a CM_CONFIRM_SEND indicator to the partner TP through the *status_received* parameter of a [Receive](./receive-cpi-c-2.md) call, because the synchronization level is set to CM_CONFIRM. This indicator tells the partner TP that a [Confirmed](./confirmed-cpi-c-2.md) response is expected before the partner TP can begin to send data.  
  
## Changing to SEND State  
 The [Request_To_Send](./request-to-send-cpi-c-1.md) call informs the partner TP (for which the conversation is in SEND state) that the local TP (for which the conversation is in RECEIVE state) wants to send data. This request is communicated to the partner TP through the *request_to_send_received* parameter of the [Confirm](./confirm-cpi-c-2.md) call. (The *request_to_send_received* parameter is also returned to [Send_Data](./send-data-cpi-c-2.md) and other calls.)  
  
 When the partner TP issues the [Prepare_To_Receive](./prepare-to-receive-cpi-c-1.md) call, the conversation state changes to RECEIVE for the partner TP, making it possible for the local TP to send data.  
  
> [!IMPORTANT]
>  Issuing [Request_To_Send](./request-to-send-cpi-c-1.md) does not change the state of the conversation. Upon receiving a request to send, the partner TP is not required to change the conversation state. It can ignore the request.