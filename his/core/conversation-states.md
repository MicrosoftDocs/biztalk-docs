---
title: "Conversation States1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7b52ce78-16ae-4957-b97f-53656ee49c82
caps.latest.revision: 3
---
# Conversation States
The state of the conversation (as viewed by a particular TP) governs which APPC verbs the TP can issue at a particular time. For example, a TP cannot issue [MC_SEND_DATA](../Topic/MC_SEND_DATA2.md) if the conversation is not in SEND state for that TP.  
  
 The state of a conversation depends on the TP from which it is viewed. A local TP can view a conversation as being in SEND state while the partner TP views the conversation as being in RECEIVE state. A particular TP can be in several conversations, each of which is in a different state.  
  
 The possible conversation states are summarized here.  
  
 **CONFIRM**  
 The TP has received a request for confirmation of receipt of data; it must respond positively or send error information to the partner TP.  
  
 **CONFIRM_DEALLOCATE**  
 The TP has received a request for confirmation; it must respond positively or send error information. If the TP responds positively, the conversation is automatically deallocated.  
  
 **CONFIRM_SEND**  
 The TP has received a request for confirmation; it must respond positively or send error information. After responding, the TP can begin to send data.  
  
 **PENDING_POST**  
 The TP is receiving data asynchronously. The TP can perform other processing not related to this conversation.  
  
 **RECEIVE**  
 The TP can receive application data and status information from the partner TP. When the conversation is in RECEIVE state, the TP can also send error information and request permission to send data.  
  
 **RESET**  
 The conversation has not started or has been terminated.  
  
 **SEND**  
 The TP can send data to the partner TP and request confirmation. When the conversation is in SEND state, the TP can also begin to receive data, which changes the state to RECEIVE.  
  
 **SEND_PENDING**  
 The TP issued a receive verb and the **what_rcvd** parameter returned by that verb indicated both data received and a status indication of SEND. This only affects the use of the **err_dir** parameter for [SEND_ERROR](../Topic/SEND_ERROR1.md) and [MC_SEND_ERROR](../Topic/MC_SEND_ERROR1.md). Otherwise, the state is the same as the SEND state.  
  
 This section contains:  
  
-   [State Checks](../core/state-checks.md)  
  
-   [Changing Conversation States](../core/changing-conversation-states.md)