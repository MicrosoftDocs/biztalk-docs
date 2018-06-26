---
title: "The MessageBox Database | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "messages, MessageBox database"
  - "messages, suspended messages"
  - "MessageBox database, messages"
  - "MessageBox database, about MessageBox database"
  - "MessageBox database, suspended messages"
  - "suspended messages"
  - "MessageBox database"
  - "suspended messages, MessageBox database"
ms.assetid: f89eb02c-1b83-4127-8a91-e78fb4a1f96e
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# The MessageBox Database
The heart of the publish/subscribe engine in Microsoft BizTalk Server is the MessageBox database. The MessageBox is made up of two components: one or more Microsoft SQL Server databases and the Messaging Agent. The SQL Server database provides the persistence store for many things including messages, message parts, message properties, subscriptions, orchestration state, tracking data, host queues for routing, and others. The BizTalk Server group may have one or more MessageBox databases into which it publishes messages and from which subscribers to those messages extract messages.  
  
 The database provides some of the logic related to routing messages and fulfilling subscriptions. The Message Agent, however, is the component that encapsulates and abstracts the database component and is the interface used by BizTalk Server to interact with the MessageBox. The Message Agent is a Component Object Model (COM) component that provides interfaces for publishing messages, subscribing to messages, retrieving messages, and so on. This interface is the only mechanism used by other BizTalk Server components, including the adapter framework and orchestrations, to interact with the MessageBox.  
  
## The MessageBox and the Message  
 A MessageBox database subscription is a set of established information and service information. The established (or predicate) information is the criteria that a message must meet. The service information is what to do with the message that meets the criteria. All of this information is stored in a set of tables that call the messaging and orchestration engine.  
  
 When BizTalk Server receives a message, it processes the message in a pipeline, and places the message in the MessageBox database. The incoming message has a context. The message context is a set of properties associated with the message. The three types of message context properties are:  
  
- Simple written properties  
  
- Promoted properties  
  
- Predicate properties  
  
  The promoted and predicate message properties indicate the business process that subscribes to this message, and whether the business process has the permissions necessary to receive the message.  
  
  If a business process subscribes to the message, the MessageBox database sends the message to the business process. When the business process receives the message, it processes the message on an available host instance. After processing the message, if the business process subscribes to a pipeline or send port, the business process sends a return message to the MessageBox database.  
  
  For each BizTalk Host, the associated MessageBox has one work queue and one suspended queue. Additionally, each MessageBox database contains a set of tables for static states, dynamic states, and instance state. For information about BizTalk Hosts, see [Entities](../core/entities.md).  
  
> [!IMPORTANT]
>  If a host becomes unavailable --for example, the MessageBox database that receives messages from that host becomes unavailable, all other MessageBox databases become unavailable.  
  
 You create the first MessageBox database when you run the Configuration Wizard. The MessageBox database that is configured becomes the master MessageBox database. The master MessageBox database evaluates and routes subscriptions to all other MessageBox databases in the BizTalk Server environment. For information about improving performance for the master MessageBox database, see [Managing MessageBox Databases](../core/managing-messagebox-databases.md).  
  
> [!IMPORTANT]
>  You must use SQL Server clustering to provide failover protection for MessageBox databases.  
  
## Suspended Messages in the MessageBox Database  
 BizTalk Server stores messages associated with suspended pipelines in the MessageBox database. If a failure occurs in the pipeline, BizTalk Server suspends the instance of a message. There are two types of suspended service instances:  
  
- Suspended instances that you can resume.  
  
- Suspended instances that you cannot resume. For example, if an instance is corrupt.  
  
  Depending on the cause of the suspension, you may be able to resume services that BizTalk Server suspends -- for example, if an orchestration hits a Suspend shape, or if a transport was unable to deliver a message, BizTalk Server does not automatically remove suspended instances that you cannot resume from the MessageBox database. You can choose to save a service instance to disk before removing it from the suspended queue.  
  
  For information about backing up MessageBox databases, see [Backing Up and Restoring BizTalk Server Databases](../core/backing-up-and-restoring-biztalk-server.md).  
  
## See Also  
 [The Messaging Engine](../core/the-messaging-engine.md)