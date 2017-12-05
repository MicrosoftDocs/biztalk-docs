---
title: "Conversation States (CPI-C)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a741b036-cd1f-45eb-ac6d-705a90327a51
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Conversation States (CPI-C)
The state of the conversation (as viewed by a particular transaction program (TP)) governs which Common Programming Interface for Communications (CPI-C) calls can be made by the TP at a particular time. For example, a TP cannot issue [Send_Data](../core/send-data-cpi-c-1.md) if the conversation is not in SEND or SEND_PENDING state for that TP.  
  
 The state of a conversation depends on the TP from which it is viewed. A local TP can view a conversation as being in SEND state while the partner TP views the conversation as being in RECEIVE state. A particular TP can be in several conversations, each of which is in a different state.  
  
 The possible conversation states are summarized in this topic.  
  
 CONFIRM  
 The TP has received a request for confirmation of receipt of data. It must respond positively or send error information to the partner TP.  
  
 CONFIRM_DEALLOCATE  
 The TP has received a request for confirmation and must respond positively or send error information. If the TP responds positively, the conversation is automatically deallocated.  
  
 CONFIRM_SEND  
 The TP has received a request for confirmation. It must respond positively or send error information. After responding, the TP can begin to send data.  
  
 INITIALIZE  
 The conversation has been initialized successfully.  
  
 RECEIVE  
 The TP can receive application data and status information from the partner TP. When the conversation is in RECEIVE state, the TP can also send error information and request permission to send data.  
  
 RESET  
 The conversation has not started or has been terminated.  
  
 SEND  
 The TP can send data to the partner TP and request confirmation. When the conversation is in SEND state, the TP can also begin to receive data, which can cause the state to change to RECEIVE.  
  
 SEND_PENDING  
 The TP issued a [Receive](../core/receive-cpi-c-1.md) call and received data as well as a send indicator (*status_received* = CM_SEND_RECEIVED), indicating that the TP can begin to send data. This state differs from the SEND state, which occurs when the TP receives data on one **Receive** call and the send indicator on a subsequent **Receive** call.  
  
 This section contains:  
  
-   [State Checks](../core/state-checks-cpi-c-1.md)  
  
-   [Changing Conversation States](../core/changing-conversation-states-cpi-c-2.md)