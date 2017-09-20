---
title: "Processing in the OrderBroker Orchestration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "orchestrations, examples"
  - "orchestrations, nested scopes"
  - "nested scopes, performance"
  - "processing, examples"
  - "nested scopes, orchestrations"
  - "orchestrations, performance"
  - "performance, orchestrations"
  - "performance, nested scopes"
  - "examples, orchestration processing [process management solution]"
  - "scopes, nesting"
ms.assetid: c296e00c-b3ad-4161-baf7-258899185c34
caps.latest.revision: 23
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Processing in the OrderBroker Orchestration
This section describes how the **OrderBroker** orchestration takes orders and prepares them for a process manager. The section begins by discussing the general workings of the orchestration. The next part discusses how the orchestration processes a message. It then highlights how the orchestration uses an atomic transaction to improve performance.  
  
> [!NOTE]
>  Because of the length of the length of the **OrderBroker** code, you may want to read this section with the orchestration open in Microsoft® Visual Studio.  
  
## Why an Order Broker?  
 The purpose of the **OrderBroker** orchestration is to preprocess an order and route it to the correct process manager. Pre-processing here consists of producing informational messages for the history database, for the servicing system, and to acknowledge receipt of the order. The **OrderBroker** also creates a generic order message from the customer service request. This normalization of the order allows for generic consumption of the order by elements of the business process.  
  
 The order message is a multipart message with routing information separated from the order information. The routing information is also generic and designed to be consumed by any order manager. This, in turn, makes it easier to expand the solution. For information about multi-part messages, see [How to Use Multi-part Message Types](../core/how-to-use-multi-part-message-types.md).  
  
 Isolating the brokering function also allows you to move it to another BizTalk group. Because the **OrderBroker** publishes to the MessageBox database—that is, it is direct-bound—also makes it easier to put the broker in another group --you can move the broker without changing the orchestration. For more information about putting the **OrderBroker** in another group, see [Communication between OrderBroker and OrderManager](../core/communication-between-orderbroker-and-ordermanager.md).  
  
> [!NOTE]
>  The **OrderBroker** orchestration, because it has only one **OrderManager** to communicate with, simply assigns a constant string to the **OrderMgrType** field in the order manager message. Typically, in an application where there were multiple order managers, the application would use the Business Rule Engine to determine the proper value for this field and the order routing. For more information about the Business Rule Engine, see [Creating and Using Business Rules](../core/creating-and-using-business-rules.md).  
  
## Order Processing  
 The **OrderBroker** orchestration begins with two **Receive** shapes within a **Listen** shape. One **Receive** shape takes messages from the customer support system; the other, messages from the vendor system. Messages from either source have the same schema.  
  
 The orchestration extracts the return address from the message and uses it to set the address for the dynamic port, **CSRPort**. The orchestration uses this port to send acknowledgement and error messages.  
  
 The next steps in the **OrderBroker** orchestration create the history message, the service message, the confirmation message, and the order message to send to the **OrderManager** orchestration. The orchestration uses the **InsertOrderBody** utility function to add the order message to the history message.  
  
> [!NOTE]
>  In some situations the solution may produce messages that are delivered but not consumed. The order broker orchestration uses a send port to insert information in the history database. This send port uses delivery notification. Configuration maps the send port to a send port group containing two ports—one port for the test configuration (**HistoryInsert-Test-SP**), one for the regular configuration (**HistoryInsert-SP**). If you leave both ports in the group running, the solution sends messages on both ports. It thus requests two delivery notifications but processes only one.  
>   
>  To avoid this situation, unenlist the test port (**HistoryInsert-Test-SP**), or stop the test version of the application, **BTSScn.BPM.OrderBrokerApp.Test**. For more information about delivery notifications, see [Using Acknowledgments](../core/using-acknowledgments.md).  
  
 When constructing the message to send to the **OrderManager** orchestration, the **OrderBroker** orchestration creates a multi-part message with two parts. One part contains the routing information; the other, the order itself. The routing part of the message, **OrderMgrMsg.Routing**, uses a schema defined by a C# class in the **SchemaClasses** assembly. The broker treats the order part of the message as a generic, or type-agnostic, XML document (**System.Xml.XmlDocument**) and assigns it to **OrderMgrMsg.Order**.  
  
 There are two fields in the routing information that are especially important to the order manager, **OrderMgrMsg.Routing.OrderMgrType** and **OrderMgrMsg.Routing.Status**. The broker sets the **OrderMgrType** to the type of the order manager that is to handle the order. In the solution, there is only one order manager and the field is set to CABLEORDER. The broker also sets the **Status** field to ACCEPTED. This is the value that tells the order manager the message is a new order. The order manager in the solution, **OrderManager** orchestration, uses a **Receive** shape that filters for the order type equal to CABLEORDER and status equal to ACCEPTED.  
  
 The remaining steps in the **OrderBroker** orchestration send the different messages to the appropriate ports.  
  
## Improving Performance with Nested Scopes  
 One of the noticeable things about the **OrderBroker** orchestration is its use of nested scopes. The nested scopes are there, in part, to improve performance by limiting the persistence points.  
  
 The orchestration engine periodically saves the state of the entire orchestration at execution points called persistence points. The orchestration engine automatically treats several orchestration shapes, including **Send** shapes, as persistence points. For a list of persistence points and more information about them, see [Persistence and the Orchestration Engine](../core/persistence-and-the-orchestration-engine.md).  
  
 With five **Send** shapes, the **OrderBroker** orchestration should have five persistence points. However, when you group **Send** shapes inside an atomic transaction scope, the engine recognizes it only needs one persistence point for the scope. Because four of the **Send** shapes in **OrderBroker** orchestration are not part of exception handlers and nothing needs to be done after the send, they can go in an atomic transaction scope. This reduces the number of persistence points. For more information about atomic transactions, see [Atomic Transactions](../core/atomic-transactions.md).  
  
 In addition, the orchestration engine will use a single persistence point for nested transactions if the transactions all end at the same time. Thus, the way **OrderBroker** orchestration nests transactions further reduces the persistence points: the orchestration has a single persistence point due to the use of **Scope** shapes.  
  
> [!TIP]
>  You can improve performance by minimizing the number of persistence points in an orchestration. You can group **Send** shapes in an atomic transaction to produce a single persistence point for all of the **Send** shapes. Ending nested transaction scopes at the same time produces a single persistence point for the transactions.  
  
 An atomic transaction scope cannot have an exception handler. Because of this, the orchestration nests the atomic scope inside a long running transaction. This outer transaction can have an exception handler and it is this handler that processes an exception from the **Send** shapes.  
  
> [!TIP]
>  Nesting an atomic transaction inside a long running transaction is a common pattern to allow for exception handling.  
  
## See Also  
 [Processing in the Business Process Management Solution](../core/processing-in-the-business-process-management-solution.md)   
 [Process Manager Logic](../core/process-manager-logic.md)   
 [Interrupt Handling in the Business Process Management Solution](../core/interrupt-handling-in-the-business-process-management-solution.md)   
 [The ExceptionHandler Orchestration](../core/the-exceptionhandler-orchestration.md)