---
description: "Learn more about: Processing in the Business Process Management Solution"
title: "Processing in the Business Process Management Solution"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Processing in the Business Process Management Solution
This section describes how the Business Process Management Solution works: how it processes orders, how it makes use of interrupts, and how it handles exceptions so that actions can be retried.  
  
 Order processing relies on two main orchestrations, **OrderBroker** and **OrderManager**. The **OrderBroker** orchestration is written so that there can be multiple order manager orchestrations, one for each kind of order. The solution includes only one **OrderManager**. It, too, is relatively generic so that it can be adapted to other types of orders.  
  
## In This Section  
  
-   [Processing in the OrderBroker Orchestration](../core/processing-in-the-orderbroker-orchestration.md)  
  
-   [Process Manager Logic](../core/process-manager-logic.md)  
  
-   [Processing in the Order Processing Stages](../core/processing-in-the-order-processing-stages.md)  
  
-   [Interrupt Handling in the Business Process Management Solution](../core/interrupt-handling-in-the-business-process-management-solution.md)  
  
-   [Exception Handling in the Business Process Management Solution](../core/exception-handling-in-the-business-process-management-solution.md)
