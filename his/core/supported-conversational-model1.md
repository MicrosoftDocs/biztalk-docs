---
description: "Learn more about: Supported Conversational Model"
title: "Supported Conversational Model1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Supported Conversational Model
TI supports only the nonconversational (ping-pong) model. A mainframe transaction program (TP) may not expect a request-reply (ping-pong) nonconversational sequence like that required by TI, in which case, you will need to modify the mainframe TP. The mainframe TP may be set up to communicate with other TPs by using the conversational or pseudo conversational models, neither of which are supported by TI.  
  
 In a nonconversational transaction, the entire exchange of data between the client and server occurs within a single method call. The exchange of data can be fairly complex (for example, if recordsets are used), but the base application has no opportunity to delay the exchange of data or otherwise cause the conversation to remain idle.  
  
 A pseudo-conversational TP attempts to get conversational-type client/server interactions while avoiding the scalability problems associated with true conversations. Pseudo-conversations are implemented by TPs that maintain state for clients over a series of nonconversational requests. An application-specific context handle is used to retrieve the saved state over the course of the pseudo-conversation. TI does not support the pseudo-conversational model.  
  
## See Also  
 [WIP Programming Model](../core/wip-programming-model2.md)
