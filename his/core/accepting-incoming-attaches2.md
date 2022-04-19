---
description: "Learn more about: Accepting Incoming Attaches"
title: "Accepting Incoming Attaches2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 51ffc914-aad1-4a75-be5c-c8bfb074b026
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Accepting Incoming Attaches
The Sync Point support in Host Integration Server is intended for use only by gateway applications that implement the architected SNA Sync Point components, including Conversation-Protected Resource Manager (C-PRM). In a Sync Point implementation, it is necessary for C-PRM to be aware of all protected conversations, both locally initiated and remotely initiated. This can be achieved in Host Integration Server by C-PRM intercepting the conversation allocation and deallocation verbs and issuing them on behalf of the transaction program (TP). Note that since Host Integration Server does not allow TP or conversation identifiers to be shared across processes, this also means that the process containing C-PRM must also intercept all APPC verbs issued by the client TPs.  
  
 For locally initiated TPs, this is straightforward. However for incoming Attaches, the situation is made more complex by the requirement that the [RECEIVE_ALLOCATE](receive-allocate1.md) verb specify the name of the TP to be matched with the Attach.  
  
 In some implementations, this will not be an issue, as the gateway will be aware of the names of all the transactions passing through it. To support this situation, the **RECEIVE_ALLOCATE** verb has been enhanced as described in the following topic to permit the gateway to indicate that it can accept Sync Point conversations.  
  
 In other implementations, the gateway does not know the names of the transactions passing through it. This is particularly so when the gateway is providing a conversion between SNA and another communications protocol. In this case, Host Integration Server allows the gateway process to register itself as a Sync Point Attach Service, indicating that it is willing to accept incoming Attaches for any Sync Point conversation. In this case, the gateway must be implemented as a [Sync Point Attach Manager](../core/sync-point-attach-manager2.md).  
  
 This section contains:  
  
-   [Sync Point Knows Transaction Names](../core/sync-point-knows-transaction-names2.md)  
  
-   [Sync Point Attach Manager](../core/sync-point-attach-manager2.md)  
  
-   [Rejecting Remotely Initiated Conversations](../core/rejecting-remotely-initiated-conversations1.md)
