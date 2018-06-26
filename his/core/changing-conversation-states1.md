---
title: "Changing Conversation States1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ee197ab7-6422-4ddf-a3cb-676c2e02be67
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Changing Conversation States
A change in the conversation state can result from:  
  
- A verb issued by the local TP.  
  
- A verb issued by the partner TP.  
  
- An error condition.  
  
  The following example shows how APPC verbs can change the state of the conversation from SEND to RECEIVE and from RECEIVE to SEND.  
  
> [!NOTE]
>  Any TP can send or receive data, regardless of whether it is the invoking TP (the TP that started the conversation) or the invokable TP (the TP that responded to a request to start a conversation).  
  
 This example shows how APPC verbs can change the conversation state. In this table, each conversation state appears in bold and precedes the APPC verbs that are used while in that state.  
  
|Issued by the invoking TP|Issued by the invokable TP|  
|-------------------------------|--------------------------------|  
|TP_STARTED||  
|**Conversation state: RESET**||  
|MC_ALLOCATE||  
|(synclevel=AP_CONFIRM_SYNC_LEVL)||  
|**Conversation state: SEND**||  
|MC_SEND_DATA||  
|MC_PREPARE_TO_RECEIVE||  
|(ptr_type=AP_SYNC_LEVEL)||  
||**Conversation state: RESET**|  
||RECEIVE_ALLOCATE|  
||**Conversation state: RECEIVE**|  
||MC_RECEIVE_AND_WAIT|  
||(primary_rc=AP_OK)|  
||(what_rcvd=AP_DATA_COMPLETE)|  
||MC_RECEIVE_AND_WAIT|  
||(primary_rc=AP_OK)|  
||(what_rcvd=AP_CONFIRM_SEND)|  
||**Conversation state: CONFIRM_SEND**|  
||MC_CONFIRMED|  
||**Conversation state: SEND**|  
||MC_SEND_DATA|  
||MC_CONFIRM|  
|**Conversation state: RECEIVE**||  
|MC_RECEIVE_AND_WAIT||  
|(primary_rc=AP_OK)||  
|(what_rcvd=AP_DATA_COMPLETE)||  
|MC_RECEIVE_AND_WAIT||  
|(primary_rc=AP_OK)||  
|(what_rcvd=AP_CONFIRM_WHAT_RECEIVED)||  
|**Conversation state: CONFIRM**||  
|MC_REQUEST_TO_SEND||  
|MC_CONFIRMED||  
||(rts_rcvd=AP_YES)|  
||MC_PREPARE_TO_RECEIVE|  
||(ptr_type=AP_SYNC_LEVEL)|  
|**Conversation state: RECEIVE**||  
|MC_RECEIVE_AND_WAIT||  
|(primary_rc=AP_OK)||  
|(what_rcvd=AP_CONFIRM_SEND)||  
|**Conversation state: CONFIRM_SEND**||  
|MC_CONFIRMED||  
|**Conversation state: SEND**||  
|MC_SEND_DATA||  
|MC_DEALLOCATE||  
|(dealloc_type=AP_SYNC_LEVEL)||  
||**Conversation state: RECEIVE**|  
||MC_RECEIVE_AND_WAIT|  
||(primary_rc=AP_OK)|  
||(what_rcvd=AP_DATA_COMPLETE)|  
||MC_RECEIVE_AND_WAIT|  
||(primary_rc=AP_OK)|  
||(what_rcvd=AP_CONFIRM_DEALLOCATE)|  
||**Conversation state: CONFIRM_DEALLOCATE**|  
||MC_CONFIRMED|  
|**Conversation state: RESET**|**Conversation state: RESET**|  
|TP_ENDED|TP_ENDED|  
  
## Initial States  
 Before the conversation is allocated, the state is RESET for both TPs.  
  
 In the example, after the conversation is allocated, the initial state is SEND for the invoking TP and RECEIVE for the invokable TP.  
  
## Changing to RECEIVE State  
 [MC_PREPARE_TO_RECEIVE](./mc-prepare-to-receive1.md) allows a TP to change the conversation from SEND to RECEIVE state. This verb:  
  
- Flushes the local LU's send buffer.  
  
- Sends the AP_CONFIRM_SEND indicator to the partner TP through the **what_rcvd** parameter of a receive verb. This indicator tells the partner TP that an [MC_CONFIRMED](./mc-confirmed1.md) response is expected before the partner TP can begin to send data.  
  
  Confirmation processing is performed when the following conditions are true:  
  
- The **ptr_type** parameter is set to AP_SYNC_LEVEL.  
  
- The synchronization level of the conversation is set to AP_CONFIRM_SYNC_LEVEL.  
  
  For more information about confirmation processing, see [Confirmation Processing](../core/confirmation-processing2.md).  
  
> [!NOTE]
>  Issuing [MC_RECEIVE_AND_WAIT](./mc-receive-and-wait2.md) while the conversation is in SEND state flushes the LU's send buffer and changes the conversation state to RECEIVE. Changing the conversation state in this manner does not support confirmation processing.  
  
## Changing to SEND State  
 [MC_REQUEST_TO_SEND](./mc-request-to-send1.md) informs the partner TP (for which the conversation is in SEND state) that the local TP (for which the conversation is in RECEIVE state) wants to send data. This request is communicated to the partner TP through the **rts_rcvd** parameter of [MC_CONFIRM](./mc-confirm2.md). (The **rts_rcvd** parameter is also returned to [MC_SEND_DATA](./mc-send-data1.md) and other verbs.)  
  
 When the partner TP issues [MC_PREPARE_TO_RECEIVE](./mc-prepare-to-receive1.md), the conversation state changes to RECEIVE for the partner TP, making it possible for the local TP to send data.  
  
> [!NOTE]
>  Issuing [MC_REQUEST_TO_SEND](./mc-request-to-send1.md) does not change the state of the conversation. Upon receiving a request to send, the partner TP is not required to change the conversation state; it can ignore the request.