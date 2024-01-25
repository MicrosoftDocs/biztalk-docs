---
description: "Learn more about: Interrupt Handling in the Business Process Management Solution"
title: "Interrupt Handling in the Business Process Management Solution"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Interrupt Handling in the Business Process Management Solution
This section describes the interrupt handling mechanism used in the Business Process Management Solution. Using the interrupt mechanism enables you to halt order processing when an order is updated or canceled.  
  
## Interrupt Handling  
 The orchestrations that implement the processing stages call an orchestration, **CheckInterrupt**, that tests for an interrupt request from some other part of the process. The **CheckInterrupt** orchestration consists of a **Listen** shape. One branch of the **Listen** shape checks for a message with the same correlation ID as the current order. If there is such a message, the **CheckInterrupt** orchestration sends an acknowledgement message and executes a **Throw** shape. Because the branches in a **Listen** shape are executed from left to right, the delay appears in the right branch. Notice that the delay is zero (0).  
  
 The combination of the **Listen** shape, a receive branch, and a delay branch allows the orchestration to check for messages. If there is an interrupt message, the left branch executes. If there is no message, the right branch executes and returns to the calling orchestration. An interrupt message can be sent at any time. Because the **CheckInterrupt** orchestration is run only occasionally, there may be an interrupt message waiting for it.  
  
 The **OrderManager** sets interrupts by calling the **Interrupter** orchestration. The **Interrupter** orchestration sends an interrupt message to the **InterruptPort** and waits for a reply. The orchestration uses the **Timeout** property of the enclosing **Scope** shape to restart the loop if a reply isn't received. The orchestration continues to send the interrupt message as long as the scope times out before receiving a reply. A timeout indicates that the request matched a subscription, but there hasn't been time for a reply. The loop ends if there is a reply, or if there is no subscription to the **InterruptPort**.  
  
 The request-response-completion pattern the **OrderManager** uses with the process stages is a critical part of the interrupt handling. Because the **OrderManager** waits for a response—an acknowledgement—from the stage, it knows that the stage has started running before continuing. This guarantees that a stage cannot receive an interrupt before it starts. This also lets the **OrderManager** know that, if there is no subscription to an interrupt, the stage has completed.  
  
## See Also  
 [Processing in the Business Process Management Solution](../core/processing-in-the-business-process-management-solution.md)   
 [Process Manager Logic](../core/process-manager-logic.md)   
 [The ExceptionHandler Orchestration](../core/the-exceptionhandler-orchestration.md)
