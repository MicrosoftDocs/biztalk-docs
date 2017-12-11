---
title: "Accepting Incoming Attaches1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 54d76a08-05d5-4eb7-b688-dab93741a9f1
caps.latest.revision: 3
---
# Accepting Incoming Attaches
The Sync Point support in Host Integration Server is intended for use only by gateway applications that implement the architected SNA Sync Point components, including Conversation-Protected Resource Manager (C-PRM). In a Sync Point implementation, it is necessary for C-PRM to be aware of all protected conversations, both locally initiated and remotely initiated. This can be achieved in Host Integration Server by C-PRM intercepting the conversation allocation and deallocation verbs and issuing them on behalf of the transaction program (TP). Note that since Host Integration Server does not allow TP or conversation identifiers to be shared across processes, this also means that the process containing C-PRM must also intercept all APPC verbs issued by the client TPs.  
  
 For locally initiated TPs, this is straightforward. However for incoming Attaches, the situation is made more complex by the requirement that the [RECEIVE_ALLOCATE](../HIS2010/receive-allocate2.md) verb specify the name of the TP to be matched with the Attach.  
  
 In some implementations, this will not be an issue, as the gateway will be aware of the names of all the transactions passing through it. To support this situation, the **RECEIVE_ALLOCATE** verb has been enhanced as described in the following topic to permit the gateway to indicate that it can accept Sync Point conversations.  
  
 In other implementations, the gateway does not know the names of the transactions passing through it. This is particularly so when the gateway is providing a conversion between SNA and another communications protocol. In this case, Host Integration Server allows the gateway process to register itself as a Sync Point Attach Service, indicating that it is willing to accept incoming Attaches for any Sync Point conversation. In this case, the gateway must be implemented as a [Sync Point Attach Manager](../HIS2010/sync-point-attach-manager1.md).  
  
 This section contains:  
  
-   [Sync Point Knows Transaction Names](../HIS2010/sync-point-knows-transaction-names1.md)  
  
-   [Sync Point Attach Manager](../HIS2010/sync-point-attach-manager1.md)  
  
-   [Rejecting Remotely Initiated Conversations](../HIS2010/rejecting-remotely-initiated-conversations2.md)