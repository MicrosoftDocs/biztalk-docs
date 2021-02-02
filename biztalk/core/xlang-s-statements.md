---
description: "Learn more about: XLANG-s Statements"
title: "XLANG-s Statements | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 620d0452-a8da-4285-b8b2-5a932ffcde28
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# XLANG-s Statements
XLANG/s statements generally fall into one of two categories: simple statements that act on their own, such as **receive** or **send**, and complex statements that contain or group either simple statements or other complex statements, such as **scope**, **parallel**, and **listen**. Each statement is corresponding to an orchestration shape in the BizTalk Orchestration Designer. XLANG/s defines the following statements:  
  
-   **group.** Used to group operations into a single collapsible and expandable unit for visual convenience.  
  
-   **send.** Used to send a specified message to a specified port.  
  
-   **receive.** Used to wait for the receipt of a specified message from a specified port.  
  
-   **port.** Defines where and how messages are transmitted.  
  
-   **role link.** Used to create a collection of ports that communicate with the same logical partner, perhaps through different transports or endpoints  
  
-   **transform.** Used to map the fields from existing messages into new messages.  
  
-   **message assignment.** Used to send a specified message to a specified port.  
  
-   **construct message.** Defines a block of XLANG/s code where a message is created and initialized. Existing messages can be sent to an XLANG/s program, but cannot be created outside of a construct. This mechanism provides for message distribution and rich message tracking, because a message state is known at all times.  
  
-   **call orchestration.** Synchronously calls from one orchestration to another orchestration. Parameters can be passed and returned.  
  
-   **start orchestration.** Used to enable your orchestration to call another orchestration asynchronously.  
  
-   **call rules.** Enables you to configure a Business Rules policy to be executed in your orchestration.  
  
-   **expression.** XLANG/s supports rich expression syntax to support the wide variety of usage scenarios required for protocol definition. This statement is used to assign port properties, service-link properties, messages, variables, and objects, and to invoke methods, properties, or static data fields.  
  
-   **decide.** Used to conditionally execute one of several paths of execution, depending on the value of its associated conditions.  
  
-   **delay.** Used to wait until an absolute time is reached or a relative time is reached.  
  
-   **listen.** As with a **parallel** statement, the **listen** statement has multiple paths of execution branches. However, the branches must begin with a **delay** statement or a **receive** statement. The branch that receives the first invocation is executed. The other branches of the **listen** statement are never executed.  
  
-   **parallel actions.** Executes multiple branches of a business process concurrently. All branches must complete processing before any statements following the parallel statement are executed.  
  
-   **loop.** Repeatedly executes while its associated condition remains true.  
  
-   **scope.** Provides a context for a block of code that defines variables and transactional semantics that apply to that block of code. Variable lifetime can be restricted to that scope. Transactional semantics, such as long-running, atomic, or none can be applied to a scope to affect its behavior.  
  
-   **throw exception.** Used to explicitly invoke an exception/fault handler in the current code block.  
  
-   **compensate.** Used to explicitly invoke a compensation block associated with a given scope. A **scope** statement may have one or more compensation blocks associated with it. The **compensate** statement directs execution to the selected compensation block.  
  
-   **suspend.** Temporarily halts execution of a process, but can be restarted by an operator or application. A string expression associated with the **terminate** statement is made available to operators/administrators through appropriate logs or through a user interface.  
  
-   **terminate.** Forcibly and irrevocably stops all processing in a schedule. A string expression associated with the **terminate** statement is made available to operators and administrators through appropriate logs or through a user interface.  
  
## See Also  
 [Orchestration Shapes](../core/orchestration-shapes.md)   
 [XLANG-s Data Types](../core/xlang-s-data-types.md)   
 [XLANG-s Variables and Operators](../core/xlang-s-variables-and-operators.md)   
 [XLANG-s Expressions](../core/xlang-s-expressions.md)   
 [XLANG-s Reserved Words](../core/xlang-s-reserved-words.md)   
 [XLANG-s to BPEL4WS Type Conversions](../core/xlang-s-to-bpel4ws-type-conversions.md)
