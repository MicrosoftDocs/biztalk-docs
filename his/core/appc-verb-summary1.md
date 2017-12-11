---
title: "APPC Verb Summary1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aa56da55-c86a-4d3b-9aee-4a8095890c9e
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# APPC Verb Summary
This section briefly describes each APPC verb, grouped by function.  
  
## Verbs for Starting Conversations  
 [ALLOCATE](../HIS2010/allocate1.md)or [MC_ALLOCATE](../HIS2010/mc-allocate1.md)  
 Issued by the local transaction program (TP). This verb allocates a session between the local logical unit (LU) and a partner LU, and establishes a conversation between the local TP and the partner TP.  
  
 **ALLOCATE** can establish either a basic or a mapped conversation. **MC_ALLOCATE** can start only a mapped conversation. After the conversation is allocated, APPC uses this verb to return a conversation identifier (**conv_id**).  
  
 [RECEIVE_ALLOCATE](../HIS2010/receive-allocate2.md)  
 Issued by the partner TP. This verb confirms that the partner TP is ready to begin a conversation with the local TP that issued **ALLOCATE** or **MC_ALLOCATE**. Upon successful execution, this verb returns a TP identifier (**tp_id**) for the partner TP and the **conv_id**.  
  
 [TP_STARTED](../HIS2010/tp-started1.md)  
 Issued by the local TP. This verb notifies APPC that the local TP is starting. Upon successful execution, this verb returns a **tp_id** for the local TP.  
  
## Verbs for Sending Data  
 [CONFIRM](../HIS2010/confirm1.md)or [MC_CONFIRM](../HIS2010/mc-confirm1.md)  
 Sends the contents of the local LU's send buffer and a confirmation request to the partner TP.  
  
 [FLUSH](../HIS2010/flush1.md)or [MC_FLUSH](../HIS2010/mc-flush2.md)  
 Flushes the local LU's send buffer, sending the contents of the buffer to the partner LU and TP. If the send buffer is empty, no action takes place.  
  
 [PREPARE_TO_RECEIVE](../HIS2010/prepare-to-receive1.md)or [MC_PREPARE_TO_RECEIVE](../HIS2010/mc-prepare-to-receive2.md)  
 Changes the state of the conversation from SEND to RECEIVE. Before changing the conversation state, this verb performs the equivalent of **FLUSH**, **MC_FLUSH**, **CONFIRM**, or **MC_CONFIRM**. After this verb has successfully executed, the local TP can receive data.  
  
 [REQUEST_TO_SEND](../HIS2010/request-to-send2.md)or [MC_REQUEST_TO_SEND](../HIS2010/mc-request-to-send2.md)  
 Informs the partner TP that the local TP wants to send data. The local TP must wait until the partner TP issues **PREPARE_TO_RECEIVE**, **MC_PREPARE_TO_RECEIVE**, **RECEIVE_AND_WAIT**, or **MC_RECEIVE_AND_WAIT**, and the conversation state changes to RECEIVE for the partner TP, before the local TP begins sending data.  
  
 [SEND_DATA](../HIS2010/send-data2.md)or [MC_SEND_DATA](../HIS2010/mc-send-data2.md)  
 Puts data in the local LU's send buffer for transmission to the partner TP.  
  
 The data collected in the local LU's send buffer is transmitted to the partner LU and partner TP when one of the following occurs:  
  
-   The send buffer fills up.  
  
-   The local TP issues **FLUSH**, **MC_FLUSH**, **CONFIRM**, **MC_CONFIRM**, **DEALLOCATE**, **MC_DEALLOCATE**, or another verb that flushes the local LU's send buffer.  
  
## Verbs for Receiving Data  
 [POST_ON_RECEIPT](http://msdn.microsoft.com/en-us/bcac5eab-07f4-474f-a822-d70bbc44448b)or [MC_POST_ON_RECEIPT](../HIS2010/mc-post-on-receipt2.md)  
 Issuing this verb allows the application to register to receive a notification when data or status arrives at the local LU without actually receiving it at the same time. This verb can only be issued while in RECEIVE state and it never causes a change in conversation state.  
  
 When the TP issues this verb, APPC returns control to the TP immediately. When the specified conditions are satisfied, the Win32® event specified as a parameter is signaled and the verb completes. Then the TP looks at the return code in the verb control block to determine whether or not any data or status notification has arrived at the local LU and issues a **RECEIVE_IMMEDIATE** or **RECEIVE_AND_WAIT** verb to actually receive the data or status notification.  
  
 [RECEIVE_AND_POST](../HIS2010/receive-and-post2.md)or [MC_RECEIVE_AND_POST](../HIS2010/mc-receive-and-post1.md)  
 Issuing this verb while the conversation is in RECEIVE state changes the conversation state to PENDING_POST and causes the local TP to receive data asynchronously. This allows the local TP to proceed with processing while data is still arriving at the local LU.  
  
 Issuing this verb while the conversation is in SEND state flushes the LU's send buffer and changes the conversation state to PENDING_POST. The local TP then begins to receive data asynchronously.  
  
 [RECEIVE_AND_WAIT](../HIS2010/receive-and-wait1.md)or [MC_RECEIVE_AND_WAIT](../HIS2010/mc-receive-and-wait1.md)  
 Issuing this verb while the conversation is in RECEIVE state causes the local TP to receive any data that is currently available from the partner TP. If no data is available, the local TP waits for data to arrive.  
  
 Issuing this verb while the conversation is in SEND state flushes the LU's send buffer and changes the conversation state to RECEIVE. The local TP then begins to receive data.  
  
 [RECEIVE_IMMEDIATE](../HIS2010/receive-immediate2.md)or [MC_RECEIVE_IMMEDIATE](../HIS2010/mc-receive-immediate1.md)  
 Receives any data that is currently available from the partner TP. If no data is available, the local TP does not wait.  
  
 [TEST_RTS](../HIS2010/test-rts1.md)or [MC_TEST_RTS](../HIS2010/mc-test-rts1.md)  
 Determines whether a **REQUEST_TO_SEND** or **MC_REQUEST_TO_SEND** or notification has been received.  
  
## Verbs for Confirming Data or Reporting Errors  
 [CONFIRMED](../HIS2010/confirmed2.md)or [MC_CONFIRMED](../HIS2010/mc-confirmed2.md)  
 Replies to a confirmation request from the partner TP. It informs the partner TP that the local TP has received and processed the data without error.  
  
 [RECEIVE_LOG_DATA](../HIS2010/receive-log-data1.md)or [MC_RECEIVE_LOG_DATA](../HIS2010/mc-receive-log-data1.md)  
 Issuing this verb allows the user to register to receive the log data associated with an inbound Function Management Header 7 (FMH7) error report. The verb passes a buffer to APPC, and any log data received is placed in that buffer. APPC continues to use this buffer as successive FMH7s arrive until it is provided with another buffer (that is, until the TP issues another **RECEIVE_LOG_DATA** or **MC_RECEIVE_LOG_DATA** specifying a different buffer or no buffer at all).  
  
 [SEND_CONVERSATION](../HIS2010/send-conversation1.md)or [MC_SEND_CONVERSATION](../HIS2010/mc-send-conversation2.md)  
 Issued by the invoking TP, this verb allocates a session between the local LU and partner LU, sends data on the session, and then deallocates the session.  
  
 [SEND_ERROR](../HIS2010/send-error1.md)or [MC_SEND_ERROR](../HIS2010/mc-send-error1.md)  
 Notifies the partner TP that the local TP has encountered an application-level error.  
  
## Verbs for Getting and Setting Information  
 [GET_ATTRIBUTES](../HIS2010/get-attributes1.md)or [MC_GET_ATTRIBUTES](../HIS2010/mc-get-attributes1.md)  
 Used by a TP to get the attributes of the conversation.  
  
 [GET_LU_STATUS](../HIS2010/get-lu-status1.md)  
 Used to report the status of a particular remote LU.  
  
 [GET_STATE](../HIS2010/get-state1.md)  
 Used by a TP to interrogate the state of a particular conversation.  
  
 [GET_TP_PROPERTIES](../HIS2010/get-tp-properties1.md)  
 Returns attributes of the TP and the current transaction.  
  
 [GET_TYPE](../HIS2010/get-type1.md)  
 Used by a TP to determine the conversation type (basic or mapped) of a particular conversation. With this information, the TP can decide whether to issue basic or mapped conversation verbs.  
  
 [SET_TP_PROPERTIES](../HIS2010/set-tp-properties1.md)  
 Used to set the attributes of the TP and the current transaction.  
  
## Verbs that Provide Management Functions  
 [ACTIVATE_SESSION](../HIS2010/activate-session1.md)  
 Activates a session between the local LU and a specified partner LU, using a specified mode.  
  
 [CNOS](../HIS2010/cnos1.md)(Change Number of Sessions)  
 Establishes APPC LU 6.2 session limits.  
  
 [DEACTIVATE_SESSION](../HIS2010/deactivate-session2.md)  
 Deactivates a particular session, or all sessions on a particular mode.  
  
 [DISPLAY](../HIS2010/display1.md)  
 Returns configuration information and current operating values for the SNA node.  
  
## Verbs for Ending Conversations  
 [DEALLOCATE](../HIS2010/deallocate1.md)or [MC_DEALLOCATE](../HIS2010/mc-deallocate1.md)  
 Deallocates a conversation between two TPs. Before deallocating the conversation, this verb performs the equivalent of **FLUSH**, **MC_FLUSH**, **CONFIRM**, or **MC_CONFIRM**.  
  
 [TP_ENDED](../HIS2010/tp-ended2.md)  
 Issued by both the local and partner TPs. It notifies APPC that the TP is ending. Issuing this verb also terminates any active conversations.