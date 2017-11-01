---
title: "APPC Conversation Verbs1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a787a2a9-950d-456e-99fc-56cc3948fc54
caps.latest.revision: 3
---
# APPC Conversation Verbs
This section describes the Advanced Program-to-Program Communications (APPC) conversation verbs. The description of each verb provides:  
  
-   A definition of the verb.  
  
-   The structure defining the verb control block (VCB) used by the verb. The structure is contained in the WINAPPC.H file. The length of each VCB field is in bytes. Fields beginning with reserv (for example, reserv2) are reserved.  
  
-   The parameters (VCB fields) supplied to and returned by APPC. A description of each parameter is provided, along with its possible values and other information.  
  
-   The conversation state(s) in which the verb can be issued.  
  
-   The state(s) to which the conversation can change upon return from the verb. Conditions that do not cause a state change are not noted. For example, parameter checks and state checks do not cause a state change.  
  
-   Additional information describing the verb.  
  
 Mapped conversation verbs are preceded by an **MC_** designator. For example, the mapped conversation verb **MC_ALLOCATE** corresponds to the basic conversation verb **ALLOCATE**.  
  
 Most parameters supplied to and returned by APPC are hexadecimal values. To simplify coding, these values are represented by meaningful symbolic constants, which are established by **#define** statements in the WINAPPC.H header file. For example, the **opcode** (operation code) member of the **mc_send_data** structure used by the **MC_SEND_DATA** verb is the hexadecimal value represented by the symbolic constant AP_M_SEND_DATA. Use only the symbolic constants when writing transaction programs (TPs).  
  
## In This Section  
  
-   [ALLOCATE](../core/allocate.md)  
  
-   [CONFIRM](../core/confirm.md)  
  
-   [CONFIRMED](../core/confirmed.md)  
  
-   [DEALLOCATE](../core/deallocate.md)  
  
-   [FLUSH](../core/flush.md)  
  
-   [GET_ATTRIBUTES](../core/get-attributes.md)  
  
-   [GET_LU_STATUS](../core/get-lu-status.md)  
  
-   [GET_STATE](../core/get-state.md)  
  
-   [GET_TYPE](../core/get-type.md)  
  
-   [MC_ALLOCATE](../core/mc-allocate.md)  
  
-   [MC_CONFIRM](../core/mc-confirm.md)  
  
-   [MC_CONFIRMED](../core/mc-confirmed.md)  
  
-   [MC_DEALLOCATE](../core/mc-deallocate.md)  
  
-   [MC_FLUSH](../core/mc-flush.md)  
  
-   [MC_GET_ATTRIBUTES](../core/mc-get-attributes.md)  
  
-   [MC_POST_ON_RECEIPT](../core/mc-post-on-receipt.md)  
  
-   [MC_PREPARE_TO_RECEIVE](../core/mc-prepare-to-receive.md)  
  
-   [MC_RECEIVE_AND_POST](../core/mc-receive-and-post.md)  
  
-   [MC_RECEIVE_AND_WAIT](../core/mc-receive-and-wait.md)  
  
-   [MC_RECEIVE_IMMEDIATE](../core/mc-receive-immediate.md)  
  
-   [MC_RECEIVE_LOG_DATA](../core/mc-receive-log-data.md)  
  
-   [MC_REQUEST_TO_SEND](../core/mc-request-to-send.md)  
  
-   [MC_SEND_CONVERSATION](../core/mc-send-conversation.md)  
  
-   [MC_SEND_DATA](../core/mc-send-data.md)  
  
-   [MC_SEND_ERROR](../core/mc-send-error.md)  
  
-   [MC_TEST_RTS](../core/mc-test-rts.md)  
  
-   [MC_TEST_RTS_AND_POST](../core/mc-test-rts-and-post.md)  
  
-   [PREPARE_TO_RECEIVE](../core/prepare-to-receive.md)  
  
-   [RECEIVE_ALLOCATE](../core/receive-allocate.md)  
  
-   [RECEIVE_ALLOCATE_EX](../core/receive-allocate-ex.md)  
  
-   [RECEIVE_ALLOCATE_EX_END](../core/receive-allocate-ex-end.md)  
  
-   [RECEIVE_AND_POST](../core/receive-and-post.md)  
  
-   [RECEIVE_AND_WAIT](../core/receive-and-wait.md)  
  
-   [RECEIVE_IMMEDIATE](../core/receive-immediate.md)  
  
-   [RECEIVE_LOG_DATA](../core/receive-log-data.md)  
  
-   [REQUEST_TO_SEND](../core/request-to-send.md)  
  
-   [SEND_CONVERSATION](../core/send-conversation.md)  
  
-   [SEND_DATA](../core/send-data.md)  
  
-   [SEND_ERROR](../core/send-error.md)  
  
-   [TEST_RTS](../core/test-rts.md)  
  
-   [TEST_RTS_AND_POST](../core/test-rts-and-post.md)