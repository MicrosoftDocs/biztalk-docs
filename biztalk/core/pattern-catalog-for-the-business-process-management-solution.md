---
title: "Pattern Catalog for the Business Process Management Solution | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Canonical Message pattern [process management solutions]"
  - "Nested Scopes pattern [process management solutions]"
  - "Filter pattern [process management solutions]"
  - "Per-Instance Pipeline Configuration pattern [process management solutions]"
  - "Translator pattern, process management solutions"
  - "patterns [process management solutions], pattern types"
  - "Interruptible Orchestration pattern [process management solutions]"
  - "Decoupled Orchestration pattern [process management solutions]"
  - "Code Retry and Exception Handling pattern [process management solutions]"
  - "Process Manager pattern [process management solutions]"
  - "Asynchronous Reply pattern [process management solutions]"
  - "Custom Exceptions pattern [process management solutions]"
  - "Message Broker pattern [process management solutions]"
  - "Coordination Using Delivery Notification pattern [process management solutions]"
  - "Convoy pattern [process management solutions]"
  - "Versioning pattern [process management solutions]"
  - "Error Routing pattern [process management solutions]"
  - "Application Reference pattern [process management solutions]"
  - "Inverse Direct Partner Binding pattern [process management solutions]"
ms.assetid: 246b109e-6006-404d-88b9-e6324ce3473c
caps.latest.revision: 24
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Pattern Catalog for the Business Process Management Solution
The patterns in the business process management solution include common patterns of programming BizTalk Server, as well as the enterprise integration patterns in preceding sections. The list in this section includes both kinds of patterns.  
  
## Pattern Types  
 The following entries briefly describe the pattern and point to other topics that describe how the solution uses the pattern. In the case of general patterns, such as a filter, entries point to more general topics.  
  
### Application Reference Patterns  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] enables an application to use the artifacts in another application within the same group by adding a reference to the other application. The Business Process Management Solution uses application references in the design of the test solution as well as in the main solution. For more information about application references in the solution, see [Some Design Principles in the Business Process Management Solution](../core/some-design-principles-in-the-business-process-management-solution.md).  
  
### Asynchronous Reply Patterns  
 Communication between the order manager and the order processing stages is asynchronous. That is, the manager continues processing until the receiving the reply. The stages use self-correlating dynamic ports to send replies to the manager. Self-correlating ports eliminate the need for the order manager to manage a correlation set. The dynamic aspect of the port allows the order manager to send to the order stage the address of the port for the reply. For more information about ports in the solution, see [Order Flow through the Process Manager](../core/order-flow-through-the-process-manager.md).  
  
### Canonical Message Patterns  
 To simplify processing a solution often translates external messages into an internal format. This format is an example of a canonical message. The order broker orchestration translates all order messages into one or more canonical order messages. The order manager orchestration and processing stages use this common order format. For more information, see [Processing in the OrderBroker Orchestration](../core/processing-in-the-orderbroker-orchestration.md).  
  
### Code Retry and Exception Handling Patterns  
 The solution centralizes much of its exception handling in the **ExceptionHandler** orchestration. The solution uses this orchestration when there is a chance, as with a dropped network connection, that the operation may succeed if retried. The orchestration uses the **Recaller** object to rerun the code that failed. For more information about the orchestration, see [Exception Handling in the Business Process Management Solution](../core/exception-handling-in-the-business-process-management-solution.md). Also see [The ExceptionHandler Orchestration](../core/the-exceptionhandler-orchestration.md). For details about the use of the **Recaller** object, see [The Recaller Object](../core/the-recaller-object.md).  
  
### Convoy Pattern  
 The order manager orchestration, OrderManager, uses the convoy pattern to catch and process subsequent changes to an order being processed. For more information about the convoy pattern in the order manager, see "Order Update" in [Order Flow through the Process Manager](../core/order-flow-through-the-process-manager.md).  
  
### Coordination Using Delivery Notification  
 The **OrderBroker** orchestration uses delivery notifications to ensure that an entry is made in the history database before the history is updated by the second order processing stage (**CableOrder2**). For more information, see "Coordinating with the Stages" in [Order Flow through the Process Manager](../core/order-flow-through-the-process-manager.md). For general information about delivery notification, see [Using Acknowledgments](../core/using-acknowledgments.md).  
  
### Custom Exceptions Pattern  
 For exceptions that cannot be retried, the solution uses the usual BizTalk Server exception handling along with custom exception handling. The custom exception handling provides more specific exception handling. It also serves as a flag between nested scopes to ensure that all parts of an operation are rolled back. For more information about the solution's use of custom exceptions, see [Custom Exceptions](../core/custom-exceptions.md). For more information about scopes, see [How to Configure the Scope Shape](../core/how-to-configure-the-scope-shape.md).  
  
### Decoupled Orchestration Patterns  
 The design of the Business Process Management solution decouples orchestrations to the maximum extent possible. Decoupling the orchestrations makes it easier to version parts of the solution and simplifies moving parts of the solution to other servers or groups. For more information about the relationship between the order broker and the order manager, see [Processing in the OrderBroker Orchestration](../core/processing-in-the-orderbroker-orchestration.md) and [Order Flow through the Process Manager](../core/order-flow-through-the-process-manager.md).  
  
### Error Routing Pattern  
 The solution uses the new BizTalk Server error reporting feature. This feature routes failed messages to a subscribing port for reporting or processing. For general information about error reporting, see [Using Failed Message Routing](../core/using-failed-message-routing.md).  
  
### Filter Pattern  
 The filter pattern selects messages meeting particular criteria for processing. In BizTalk, the filter pattern almost always becomes a filter expression on a port. For more information about filters on ports, see [Using Filters With the Receive Message Shape](../core/using-filters-with-the-receive-message-shape.md).  
  
### Interruptible Orchestration Pattern  
 The solution handles order updates or cancellations by first interrupting the current order. Orchestrations in the solution use the Interrupt orchestration to process the interrupts. For more information, see [Interrupt Handling in the Business Process Management Solution](../core/interrupt-handling-in-the-business-process-management-solution.md).  
  
### Inverse Direct Partner Binding Pattern  
 The solution reverses the use of direct binding to decouple the order processing stages from the order manager. For more information about inverse direct binding, see [Inverse Direct Partner Binding](../core/inverse-direct-partner-binding.md).  
  
### Message Broker Pattern  
 The message broker pattern allows the solution to determine the destination of a message so that the sender does not need to know the destination. The Business Process Management solution implements a message broker with the **OrderBroker** orchestration. The **OrderBroker** orchestration takes an order, determines the type of service being ordered, and routes the order to the correct order manager. For more information about message brokering in the **OrderBroker**, see [Processing in the OrderBroker Orchestration](../core/processing-in-the-orderbroker-orchestration.md).  
  
### Nested Scopes Pattern  
 The **OrderBroker** orchestration uses nested scopes in order to minimize persistence points and, thus, to improve efficiency. For more information, see "Improving Performance with Nested Scopes" in [Processing in the OrderBroker Orchestration](../core/processing-in-the-orderbroker-orchestration.md).  
  
### Per-instance Pipeline Configuration  
 Although the solution uses default pipelines, it makes extensive use of the new per-instance pipeline configuration to specify an envelope for messages. For more information, see [How to Deploy Pipelines](../core/how-to-deploy-pipelines.md) and [Components of the Business Process Management Solution](../core/components-of-the-business-process-management-solution.md).  
  
### Process Manager Pattern  
 The solution uses a relatively generic order manager to control the flow through the order processing stages. This helps to separate the business logic from the management of the order process. For more information about how the OrderManager orchestration functions as a process manager, see [Process Manager Logic](../core/process-manager-logic.md).  
  
### Terminate Shape at End of Orchestration  
 Several orchestrations use a Terminate shape to end on an error even if the orchestration would have ended normally at that point. The Terminate shape enables tracking failed instances and errors. For more information, see [Custom Exceptions](../core/custom-exceptions.md).  
  
### Translator Pattern  
 The enterprise pattern of a translator—that is, the conversion of a message from one form to another form—most often translates into a BizTalk map. For general information about BizTalk maps, see [Creating Maps Using BizTalk Mapper](../core/creating-maps-using-biztalk-mapper.md).  
  
### Versioning Patterns  
 The Business Process Management solution is designed to simplify versioning of the solution components through decoupling orchestrations and using version numbering in schema namespaces. For more information, see [Versioning the Business Process Management Solution](../core/versioning-the-business-process-management-solution.md).  
  
## See Also  
 [Patterns in the Business Process Management Solution](../core/patterns-in-the-business-process-management-solution.md)