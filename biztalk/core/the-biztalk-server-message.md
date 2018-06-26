---
title: "The BizTalk Server Message | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "messages, properties"
  - "messages, about messages"
ms.assetid: 6048c191-b495-4fdc-b547-e3e322340a49
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# The BizTalk Server Message
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is, at its core, a message-handling engine. To understand the details of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], it is important to understand messages and how they are represented, stored, and processed by BizTalk Server. The details of how BizTalk Server works with messages become easier to understand after you have gained an understanding of what a message is.  
  
 Each message in BizTalk Server is considered a multi-part message and is made up of zero or more parts. Each message with one or more parts has one of these parts identified as the body part. Each part consists of a binary chunk of data which can represent an XML document, a flat file, a serialized .NET class, or other binary stream of data. You use the body part of the message to identify the type of the message that can be used for routing.  
  
 A very important concept to understand is that all messages are immutable in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. This means that after a message is constructed, it cannot be changed. A message is considered constructed after it is placed into the MessageBox database. Any changes to the message require that a new message is created and used from that point forward. This is especially clear in the Orchestration Designer, where compilation rules force you to follow strict guidelines about constructing a message before using it, and do not allow the message to be altered outside of its construction block. If you need to change the message, you must create a new construction block that creates a message of the same type, copy the original message to the new message, and then make any changes to the new message before leaving the construction block.  
  
## Message Properties  
 In addition to the parts that make up a message, each message in the system has a set of properties that go along with it in what is known as the *message context*. These properties can be values extracted from or related to the message itself. For example, adapters put properties into the context related to the receiving of a message, such as the location at which the message was received, and the type of adapter that was used to receive the message. Properties can either be written to the context, or *promoted* into the context. The difference between these two options is that promoted properties can be used as criteria in message routing while written properties cannot.  
  
 This concept of writing or promoting values to the context is related to, but not the same as, promoting properties in the BizTalk Editor. In the BizTalk Editor, an element or attribute in a schema can be flagged as a promoted property or a distinguished field. Items that are marked with PropertyField annotations in your message schema will lead to the pipeline disassembler putting a Promoted property in the context. Items that are marked with DistinguishedField annotations in your message schema will lead to the pipeline disassembler putting a Written property into the context.  
  
 The design for promoted properties started with the design of *message correlation*: the ability to relate a message being received to an already running orchestration instance. For correlation, there is a need to define a property or set of properties that provide the link between messages in the orchestration. For example, in a purchasing process, you need to correlate messages based on the PurchaseOrderID. However, in many business cases, the name of the particular field or attribute in the messages may not match. A purchase order schema might have an element named POId, while the companion invoice schema may have an element named OrderID. To correlate messages on a named property such as PurchaseOrderID in this situation, the developer must be able to abstract the name of the property to be correlated on from the source of the value. Property schemas support this abstraction.  
  
 A *property schema* enables you to define promoted properties in a common location and have them referenced by other schemas. Like other schemas, a property schema has a namespace, but unlike other schemas, it can only have defined elements (that is, not records or attributes). Each element that is defined in the property schema has a name and type. Because the property schema may need to be referenced by more than one schema, and because the information in the property schema must be available to components at runtime, the property schema must get deployed to BizTalk Server like all other schemas. In addition to the normal schema deployment steps, information about the promoted properties is extracted and stored in the bts_documentSpec table in the Management database.  
  
 After a property schema has been created, elements and attributes with the same type (for example. integer) can be promoted as one of the named properties in the property schema.  
  
 **To complete the example case from above, a developer would perform the following steps to define the shared property needed for correlation.**  
  
1. Create a property schema and define an element of type xs:int named PurchaseOrderId.  
  
2. Create a PurchaseOrder schema and add an element or attribute of type xs:int named POId.  
  
3. Using the show promotions command in the BizTalk Editor, the developer adds the POId field to the list of promoted properties and indicates that it should be promoted as the PurchaseOrderId property defined in the property schema by selecting the PurchaseOrderId named property from the list.  
  
4. Create an Invoice schema and add an element or attribute of type xs:int named OrderId.  
  
5. Using the show promotions command in the BizTalk Editor, the developer adds the OrderId field to the list of promoted properties and indicates that it should be promoted as the PurchaseOrderId property defined in the property schema by selecting the PurchaseOrderId named property from the list.  
  
   Now that this definition exists in the document schemas, pipeline components can properly promote OrderId and POId as the named property PurchaseOrderID so that it can be used for routing and correlation. For more details on this promotion process, see the topic "Message Processing" in this document.  
  
   One of the benefits of promoted properties is that the value of the element that is promoted is available in the context of the message. This means that retrieving that value is inexpensive, as it does not require loading the message into memory to execute an XPath statement on the message. Instead, a simple property bag can be used along with a key to get the value. This type of behavior is desirable in situations other than message routing and is the reason for creating distinguished fields. While promoted properties are promoted into the message context, distinguished fields are written into the message context. Unlike promoted properties however, there is no property schema for distinguished fields. This is why distinguished fields cannot be used for routing and are therefore not available as filter criteria in a send port or orchestration receive shape. Distinguished fields can, however, be used in orchestrations to read or write values from the message context instead of having to load the message into memory and extract the value.  
  
   In addition to promoting or writing properties into the message context, message predicates can also be added to the context. Message predicates are used as a security measure in BizTalk Server and provide contextual information about the message, which must match values specified for any host that the message is to be routed to. This security measure allows you to configure your BizTalk Server environment in such a way as to allow specific hosts to be the only hosts that can receive and process particular messages. As an example, in the BizTalk Server Administration Console, a host can be configured with the thumbprint of a certificate to use for message decoding and decryption. Configuring this property creates an application property for that host in the MessageBox. Secure messages that are received and decrypted using this thumbprint are then only routed to the hosts with the thumbprint configured.  
  
## See Also  
 [Runtime Architecture](../core/runtime-architecture.md)