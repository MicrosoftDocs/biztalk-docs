---
title: "Publish and Subscribe Architecture | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "publish/subscribe architecture, publishers"
  - "architecture, publish/subscribe"
  - "publishing, publish/subscribe architecture"
  - "publish/subscribe architecture, about publish/subscribe architecture"
  - "creating, subscriptions"
  - "publish/subscribe architecture, Messaging Engine"
  - "routing, publishing"
  - "Messaging Engine, publishing"
  - "publish/subscribe architecture, subscribers"
  - "publish/subscribe architecture"
  - "subscriptions, publish/subscribe architecture"
  - "publish/subscribe architecture, creating subscriptions"
  - "subscriptions, creating"
  - "Messaging Engine, subscribing"
  - "publishing, routing"
  - "Messaging Engine, publish/subscribe architecture"
  - "publish/subscribe architecture, events"
ms.assetid: 5ed36c1f-077d-468f-a99e-60f97377cef6
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Publish and Subscribe Architecture
In a publish/subscribe design, you have three components:  
  
- Publishers  
  
- Subscribers  
  
- Events  
  
  Publishers include receive ports that publish messages that arrive in their receive locations, orchestrations that publish messages when sending messages or starting another orchestration asynchronously, and solicit/response send ports that publish messages when they receive a response from the target application or transport.  
  
  In BizTalk Server, there are two main types of subscriptions: activation and instance. An *activation subscription* is one specifying that a message that fulfills the subscription should activate, or create, a new instance of the subscriber when it is received. Examples of things that create activation subscriptions include send ports with filters or send ports that are bound to orchestrations, and orchestration receive shapes that have their Activate property set to true. An *instance subscription* indicates that messages that fulfill the subscription should be routed to an already-running instance of the subscriber. Examples of things that create instance subscriptions are orchestrations with correlated receives and request/response-style receive ports waiting for a response from BizTalk Server.  
  
  The difference between the two types of subscription at the information level is that an instance subscription includes the unique instance ID, stored in the subscription table in the master MessageBox database. When an orchestration instance or receive port completes processing, instance subscriptions are removed from the MessageBox while activation subscriptions remain active as long as the orchestration or send port is enlisted.  
  
## Creating Subscriptions  
 Subscriptions are created by service classes in BizTalk Server, which are listed in the adm_ServiceClass table in the BizTalk Server Management database. These services include the caching service; in-process and isolated messaging, hosted by the Endpoint Manager; and orchestrations/XLANG hosted by the XLANG subservice. Each of these service classes can create subscriptions and receive published messages.  
  
 A subscription is a collection of comparison statements, known as predicates, involving message context properties and the values specific to the subscription. For example, Message Type is a context property of messages and many subscriptions specify the message type in their subscription. General information about the subscription is inserted into the subscriptions table by the Message Agent while the specific predicates go into one of the following predicate tables, depending on the type of operation specified for the subscription:  
  
- BitwiseANDPredicates  
  
- EqualsPredicates  
  
- EqualsPredicates2ndPass  
  
- ExistsPredicates  
  
- FirstPassPredicates  
  
- GreaterThanOrEqualsPredicates  
  
- GreaterThanPredicates  
  
- LessThenOrEqualsPredicates  
  
- LessThenPredicates  
  
- NotEqualsPredicates  
  
  All of this is accomplished by calling the Bts_CreateSubscription_\<application name\> and Bts_InsertPredicate_\<application name\> stored procedures in the MessageBox database where \<application name\> is the name of the BizTalk host that is creating the subscription.  
  
  When a send port is enlisted, the port creates, at a minimum, a subscription for any message with that send port's transport ID in the context. This allows the send port to always receive messages intended specifically for it. When an orchestration port is bound to a particular send port, the information about that binding is stored in the BizTalk Management database. When messages are sent from the orchestration through the port bound to the physical send port, the Transport ID is included in the context so that the message gets routed to that send port. However, it is important to note that this send port is not the only send port that can receive messages sent from the orchestration. When an orchestration sends a message, that message is published to the MessageBox with all of the relevant promoted properties. The bound send port is guaranteed to receive a copy of the message because the transport ID is in the context, but any other send port, or orchestration, can have a subscription that also matches the message properties. It is very important to understand that any time a message is published directly to the MessageBox, all subscribers with matching subscriptions will receive a copy of the message.  
  
## Publishing and Routing  
 After a subscription is created and enabled, a message must be published before any processing takes place. Messages are published when they are received into BizTalk Server from one of the services mentioned previously. For this discussion of routing, we will focus on messages received into BizTalk Server through an adapter.  
  
 When messages go through the receive pipeline processing, properties are promoted into the message context. After a message is ready to be published into the MessageBox after being processed by the receive adapter and pipeline, the first thing that happens is the Message Agent inserts the property values for the promoted properties and predicate values from the message context into the master MessageBox SQL Server database. Having these values in the database enables the Message Agent to make routing decisions.  
  
 The next step is for the Message Agent to ask the master MessageBox database to find subscriptions for the current batch of messages being published. Keep in mind that the messages have not yet been written to the database, only the properties from the context. The bts_FindSubscriptions stored procedure in the MessageBox queries the subscription and predicate tables identified above, linking them to the message properties stored for the current batch of messages.  
  
 With this information, the Message Agent inserts the message once into each MessageBox database that has a subscription by calling the bts_InsertMessage stored procedure. The bts_InsertMessage stored procedure is first called with a subscription ID. On this first pass, the stored procedure calls the int_EvaluateSubscriptions stored procedure which is responsible for looking up the subscription detail information, verifying that the message meets security requirements for the application by checking that message predicates match application properties for the host, and inserting a reference to the message in the application specific queue or application specific suspended queue depending on the state. The message ID, subscription ID, service ID, and other subscription information are inserted into the application specific queue table for each subscription that was found for this application. After the messages are inserted, the message properties and message predicates tables are cleared of the batch related values.  
  
 The bts_InsertMessage stored procedure is called subsequently for each part in the message. On the first call, the message context is passed and is then inserted into the SPOOL table along with metadata about the message such as the number of parts, the body part name and ID. In addition the message body part is inserted into the PARTS table using the int_InsertPart stored procedure. The bts_InsertMessage stored procedure is then called for each of the remaining message parts where they are simply passed to the int_InsertPart stored procedure to be persisted in the PARTS table.  
  
 When messages are routed, references are added for each service that receives the specific instance of the message and its parts by inserting records into the following tables:  
  
- MessageRefCountLog1  
  
- MessageRefCountLog2  
  
- PartRefCountLog1  
  
- PartRefCountLog2  
  
  These references keep the messages and parts from being deleted by cleanup jobs that run periodically to keep the MessageBox from getting full with message data for messages that are no longer in the system. Two tables are used to reduce contention and locking issues.  
  
  Now that the message has been routed to the right queue, stored in the Spool and Parts tables, and referenced in the application specific queues, the messages must be pulled off the queues by the application instances. Each host instance has a number of dequeuing threads that continuously poll the database on an interval that is configured in the adm_ServiceClass table in the BizTalk Management database. This same table has a column to indicate the number of dequeuing threads to be used. Each thread calls into the MessageBox database and calls the bts_DequeueMessages_\<application name\> stored procedure appropriate for the host application it is running in. This stored procedure uses locking semantics to make sure that only one instance and one dequeuing thread are able to operate on a message in the queue at a given time. The host instance that gets the lock gets the message, and is then responsible for handing the message to the subservice for which it is intended.  
  
  If the service receiving the message is the Endpoint Manager, then the send port is invoked (or the response portion of a request/response receive port) and if it is the XLANG/s subservice, an orchestration is either created, or located to service the subscription depending on whether there is an instance ID in the subscription. The service then releases the reference to the message and its part so that if no other services have references, the message data can be deleted.  
  
## See Also  
 [The Messaging Engine ](../core/the-messaging-engine.md)