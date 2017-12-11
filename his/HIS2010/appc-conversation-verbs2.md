---
title: "APPC Conversation Verbs2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 934302fd-bbc2-418d-8a66-8672a973cb63
caps.latest.revision: 4
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
  
-   [ALLOCATE](../HIS2010/allocate1.md)  
  
-   [CONFIRM](../HIS2010/confirm1.md)  
  
-   [CONFIRMED](../HIS2010/confirmed2.md)  
  
-   [DEALLOCATE](../HIS2010/deallocate1.md)  
  
-   [FLUSH](../HIS2010/flush1.md)  
  
-   [GET_ATTRIBUTES](../HIS2010/get-attributes1.md)  
  
-   [GET_LU_STATUS](../HIS2010/get-lu-status1.md)  
  
-   [GET_STATE](../HIS2010/get-state1.md)  
  
-   [GET_TYPE](../HIS2010/get-type1.md)  
  
-   [MC_ALLOCATE](../HIS2010/mc-allocate1.md)  
  
-   [MC_CONFIRM](../HIS2010/mc-confirm1.md)  
  
-   [MC_CONFIRMED](../HIS2010/mc-confirmed2.md)  
  
-   [MC_DEALLOCATE](../HIS2010/mc-deallocate1.md)  
  
-   [MC_FLUSH](../HIS2010/mc-flush2.md)  
  
-   [MC_GET_ATTRIBUTES](../HIS2010/mc-get-attributes1.md)  
  
-   [MC_POST_ON_RECEIPT](../HIS2010/mc-post-on-receipt2.md)  
  
-   [MC_PREPARE_TO_RECEIVE](../HIS2010/mc-prepare-to-receive2.md)  
  
-   [MC_RECEIVE_AND_POST](../HIS2010/mc-receive-and-post1.md)  
  
-   [MC_RECEIVE_AND_WAIT](../HIS2010/mc-receive-and-wait1.md)  
  
-   [MC_RECEIVE_IMMEDIATE](../HIS2010/mc-receive-immediate1.md)  
  
-   [MC_RECEIVE_LOG_DATA](../HIS2010/mc-receive-log-data1.md)  
  
-   [MC_REQUEST_TO_SEND](../HIS2010/mc-request-to-send2.md)  
  
-   [MC_SEND_CONVERSATION](../HIS2010/mc-send-conversation2.md)  
  
-   [MC_SEND_DATA](../HIS2010/mc-send-data2.md)  
  
-   [MC_SEND_ERROR](../HIS2010/mc-send-error1.md)  
  
-   [MC_TEST_RTS](../HIS2010/mc-test-rts1.md)  
  
-   [MC_TEST_RTS_AND_POST](../HIS2010/mc-test-rts-and-post2.md)  
  
-   [PREPARE_TO_RECEIVE](../HIS2010/prepare-to-receive1.md)  
  
-   [RECEIVE_ALLOCATE](../HIS2010/receive-allocate2.md)  
  
-   [RECEIVE_ALLOCATE_EX](../HIS2010/receive-allocate-ex2.md)  
  
-   [RECEIVE_ALLOCATE_EX_END](../HIS2010/receive-allocate-ex-end2.md)  
  
-   [RECEIVE_AND_POST](../HIS2010/receive-and-post2.md)  
  
-   [RECEIVE_AND_WAIT](../HIS2010/receive-and-wait1.md)  
  
-   [RECEIVE_IMMEDIATE](../HIS2010/receive-immediate2.md)  
  
-   [RECEIVE_LOG_DATA](../HIS2010/receive-log-data1.md)  
  
-   [REQUEST_TO_SEND](../HIS2010/request-to-send2.md)  
  
-   [SEND_CONVERSATION](../HIS2010/send-conversation1.md)  
  
-   [SEND_DATA](../HIS2010/send-data2.md)  
  
-   [SEND_ERROR](../HIS2010/send-error1.md)  
  
-   [TEST_RTS](../HIS2010/test-rts1.md)  
  
-   [TEST_RTS_AND_POST](../HIS2010/test-rts-and-post2.md)