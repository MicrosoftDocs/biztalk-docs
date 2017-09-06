---
title: "Using TIBCO Rendezvous Send Ports from BizTalk Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "messages, handling"
  - "message handling"
  - "BizTalk Server, using send ports from"
  - "send ports, using from BizTalk Server"
  - "messages, generating"
ms.assetid: 34e3edf7-cfc5-4c89-8069-63e8784bc9f9
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using TIBCO Rendezvous Send Ports from BizTalk Server
A transmit port can send any kind of message. When BizTalk Server sends a message through Microsoft BizTalk Adapter for TIBCO Rendezvous, the adapter generates the message based on message context properties values, or it uses the default and sends it to the specified subject.  
  
> [!NOTE]
>  According to the TIBCO Rendezvous documentation, wildcard characters are not supported in transmit subject names.  
  
## Message Handling  
 The adapter maintains a state and handles incoming BizTalk Server messages accordingly.  
  
-   If a message cannot be sent because of transport failure, BizTalk Server is instructed to resubmit later.  
  
-   If a message cannot be sent because the adapter is still initializing, the BizTalk Server message is queued. If initialization fails, BizTalk Server is instructed to resubmit later.  
  
## Message Generation  
 With the transmit adapter, BizTalk Adapter for TIBCO Rendezvous ignores the message target namespace and root element. If the adapter sends messages, it sends the payload as is. If the adapter generates a structured TIBCO Rendezvous message, the name of the root element is ignored (a message does not have a name). In every case, the adapter uses a context property to find which subject to use when publishing the message.  
  
 For more information, see [BizTalk Server Message Context Properties (Send Handlers)](../core/biztalk-server-message-context-properties-send-handlers.md) and [Data Type Mapping for Receive Handlers in TIBCO Rendezvous](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md).  
  
## See Also  
 [Creating Send Ports](../core/creating-send-ports2.md)   
 [Creating TIBCO Rendezvous Send Handlers](../core/creating-tibco-rendezvous-send-handlers.md)