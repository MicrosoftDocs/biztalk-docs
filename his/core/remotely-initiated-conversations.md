---
title: "Remotely Initiated Conversations1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d83968ce-0e52-45e1-8360-5771bcb5660d
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Remotely Initiated Conversations
Applications that want to receive remotely initiated conversations (incoming Attaches) issue a [RECEIVE_ALLOCATE](../Topic/RECEIVE_ALLOCATE2.md) verb. To accommodate Sync Point support, the **RECEIVE_ALLOCATE** verb is modified in a number of ways as follows:  
  
-   The returned **sync_level** parameter of the **RECEIVE_ALLOCATE** verb can take on a value of AP_SYNCPT, specifying that the conversation is a Sync Point conversation. The value of the **sync_level** parameter can also be determined by issuing a [GET_ATTRIBUTES](../Topic/GET_ATTRIBUTES1.md) verb on the new conversation.  
  
-   Support is added for the receipt of program initiation parameters (PIP) data by a new parameter to the **RECEIVE_ALLOCATE** verb:  
  
     The **pip_incoming** parameter is set by the application to indicate whether it is willing to accept incoming PIP data, and is returned by Host Integration Server to indicate whether PIP data is available to be received. If the application does not want to receive PIP data, this member should be set to AP_NO, the default, before issuing the **RECEIVE_ALLOCATE** verb. If it is willing to accept PIP data, this member should be set to AP_YES. On completion of the **RECEIVE_ALLOCATE** verb, this member will be set to AP_YES if PIP data is available to be received by the application and to AP_NO otherwise.  
  
-   If PIP data is available, the application can receive it by issuing one of the verbs for receiving data on completion of the [RECEIVE_ALLOCATE](../Topic/RECEIVE_ALLOCATE2.md) verb. For basic conversations, these receive verbs include [RECEIVE_AND_POST](../Topic/RECEIVE_AND_POST2.md), [RECEIVE_AND_WAIT](../Topic/RECEIVE_AND_WAIT1.md), and [RECEIVE_IMMEDIATE](../Topic/RECEIVE_IMMEDIATE2.md). On basic conversations the PIP data will be returned inclusive of the general data stream (GDS) header for PIP data (GDS identifier 0x12F5). For mapped conversations, these receive verbs include [MC_RECEIVE_AND_POST](../Topic/MC_RECEIVE_AND_POST1.md), [MC_RECEIVE_AND_WAIT](../Topic/MC_RECEIVE_AND_WAIT1.md), and [MC_RECEIVE_IMMEDIATE](../Topic/MC_RECEIVE_IMMEDIATE1.md). On mapped conversations, [!INCLUDE[hishostintegrationserver2009](../core/includes/hishostintegrationserver2009-md.md)] removes the 4-byte GDS header, and returns the PIP data only.  
  
-   For basic conversations, if the application issues a [SEND_ERROR](../Topic/SEND_ERROR1.md), [DEALLOCATE](../Topic/DEALLOCATE1.md), or [TP_ENDED](../Topic/TP_ENDED2.md) verb before the PIP data is received, the PIP data will be discarded. For mapped conversations, if the application issues an [MC_SEND_ERROR](../Topic/MC_SEND_ERROR1.md), [MC_DEALLOCATE](../Topic/MC_DEALLOCATE1.md), or **TP_ENDED** verb before the PIP data is received, the PIP data will be discarded.  
  
-   If PIP data is received for a TP that cannot or does not want to receive it, the conversation is rejected with a primary return code of AP_ALLOCATION_ERROR, and a secondary return code of AP_PIP_NOT_ALLOWED.