---
description: "Learn more about: Remotely Initiated Conversations"
title: "Remotely Initiated Conversations1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Remotely Initiated Conversations
Applications that want to receive remotely initiated conversations (incoming Attaches) issue a [RECEIVE_ALLOCATE](./receive-allocate1.md) verb. To accommodate Sync Point support, the **RECEIVE_ALLOCATE** verb is modified in a number of ways as follows:  
  
-   The returned **sync_level** parameter of the **RECEIVE_ALLOCATE** verb can take on a value of AP_SYNCPT, specifying that the conversation is a Sync Point conversation. The value of the **sync_level** parameter can also be determined by issuing a [GET_ATTRIBUTES](./get-attributes2.md) verb on the new conversation.  
  
-   Support is added for the receipt of program initiation parameters (PIP) data by a new parameter to the **RECEIVE_ALLOCATE** verb:  
  
     The **pip_incoming** parameter is set by the application to indicate whether it is willing to accept incoming PIP data, and is returned by Host Integration Server to indicate whether PIP data is available to be received. If the application does not want to receive PIP data, this member should be set to AP_NO, the default, before issuing the **RECEIVE_ALLOCATE** verb. If it is willing to accept PIP data, this member should be set to AP_YES. On completion of the **RECEIVE_ALLOCATE** verb, this member will be set to AP_YES if PIP data is available to be received by the application and to AP_NO otherwise.  
  
-   If PIP data is available, the application can receive it by issuing one of the verbs for receiving data on completion of the [RECEIVE_ALLOCATE](./receive-allocate1.md) verb. For basic conversations, these receive verbs include [RECEIVE_AND_POST](./receive-and-post1.md), [RECEIVE_AND_WAIT](./receive-and-wait2.md), and [RECEIVE_IMMEDIATE](./receive-immediate1.md). On basic conversations the PIP data will be returned inclusive of the general data stream (GDS) header for PIP data (GDS identifier 0x12F5). For mapped conversations, these receive verbs include [MC_RECEIVE_AND_POST](./mc-receive-and-post2.md), [MC_RECEIVE_AND_WAIT](./mc-receive-and-wait2.md), and [MC_RECEIVE_IMMEDIATE](./mc-receive-immediate2.md). On mapped conversations, Host Integration Server removes the 4-byte GDS header, and returns the PIP data only.  
  
-   For basic conversations, if the application issues a [SEND_ERROR](./send-error2.md), [DEALLOCATE](./deallocate2.md), or [TP_ENDED](./tp-ended1.md) verb before the PIP data is received, the PIP data will be discarded. For mapped conversations, if the application issues an [MC_SEND_ERROR](./mc-send-error2.md), [MC_DEALLOCATE](./mc-deallocate2.md), or **TP_ENDED** verb before the PIP data is received, the PIP data will be discarded.  
  
-   If PIP data is received for a TP that cannot or does not want to receive it, the conversation is rejected with a primary return code of AP_ALLOCATION_ERROR, and a secondary return code of AP_PIP_NOT_ALLOWED.
