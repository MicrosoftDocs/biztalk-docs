---
title: "Supported Conversational Model1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 96d7c400-23f2-4fd2-8c6c-b916ededf3cd
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Supported Conversational Model
TI supports only the nonconversational (ping-pong) model. A mainframe transaction program (TP) may not expect a request-reply (ping-pong) nonconversational sequence like that required by TI, in which case, you will need to modify the mainframe TP. The mainframe TP may be set up to communicate with other TPs by using the conversational or pseudo conversational models, neither of which are supported by TI.  
  
 In a nonconversational transaction, the entire exchange of data between the client and server occurs within a single method call. The exchange of data can be fairly complex (for example, if recordsets are used), but the base application has no opportunity to delay the exchange of data or otherwise cause the conversation to remain idle.  
  
 A pseudo-conversational TP attempts to get conversational-type client/server interactions while avoiding the scalability problems associated with true conversations. Pseudo-conversations are implemented by TPs that maintain state for clients over a series of nonconversational requests. An application-specific context handle is used to retrieve the saved state over the course of the pseudo-conversation. TI does not support the pseudo-conversational model.  
  
## See Also  
 [WIP Programming Model](../core/wip-programming-model.md)