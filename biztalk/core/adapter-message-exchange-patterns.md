---
description: "Learn more about: Adapter Message Exchange Patterns"
title: "Adapter Message Exchange Patterns"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Adapter Message Exchange Patterns
The BizTalk Adapter Framework supports a rich set of message exchange patterns that adapters can use in many powerful messaging scenarios.  
  
## One-Way (Asynchronous)  
 The key concept here is that messages flow in one direction.  
  
 In this message exchange pattern, messages flow one way into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] through an adapter. The Messaging Engine publishes the message into the MessageBox database. If an orchestration has an active subscription to a message of that type, the message is routed to that orchestration.  
  
 After processing the message, the orchestration publishes the message back into the MessageBox database before it is routed to an adapter to be transmitted to the specific endpoint.  
  
 When the message is submitted to the engine, no response is expected. On the outbound side, when the message is transmitted, no response is expected. This is typically referred to as asynchronous messaging and is in many ways the basic building block used by the engine for all messaging scenarios.  
  
## Request-Response Style Protocols (Sync-on-Async)  
 A request-response scenario consists of receiving a request message, processing it, and sending a response message. It is also referred to as synchronous-on-asynchronous (sync-on-async) because the underlying [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] architecture is asynchronous for scalability reasons. However, the architecture of the BizTalk Messaging Engine enables exposing a synchronous message exchange pattern on top of these asynchronous exchanges. To do this, the engine handles the complex task of correlating the request and response messages across a scaled-out architecture by linking together a number of asynchronous message exchanges to expose a synchronous interface.  
  
 For example, a Web page that checks inventory might make a SOAP call to a BizTalk SOAP receive adapter. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestrates a series of Web services that aggregate the information and return it in one SOAP response. To the client this appears to be a synchronous SOAP call, but in actuality the engine knits together a number of asynchronous message exchanges.  
  
## Solicit-Response Style Protocols  
 This scenario is initiated by sending a solicit message and completed by receiving a response message. It is referred to as solicit-response because the initial message sent is soliciting an endpoint for a response message. A scenario using this message exchange pattern might involve an orchestration making an outbound HTTP call (a solicit for a response) and waiting for the response.  
  
## Request-Multiresponse  
 This scenario is similar to the request-response scenario. However, in this scenario multiple responses may be returned for a given request. The APIs allow a time-out value to be specified, and all responses received within the time-out period are returned to the receive adapter.  
  
## Loop-Back  
 This scenario is similar to the request-response scenario. The request message is published as usual, but the engine ensures that the response message is routed back to the same adapter instance the published the request message. Because the request message is published to the MessageBox database, the tracking infrastructure ensures that both the request and response messages are tracked. This is also a good way to invoke a send pipeline processing on message then immediately get the output message send back to the adapter for subsequent processing.  
  
 An example of this scenario is a client that requires a receipt for a message. The inbound message is published to the MessageBox database. Both this message and the receipt are returned to the adapter in the same batch. In this case, the inbound message is copied with one instance being returned to the client, and the other being processed in the normal manner. This specific scenario also requires a custom XML disassembler to be written.  
  
## See Also  
 [What Is the Adapter Framework?](../core/what-is-the-adapter-framework.md)
