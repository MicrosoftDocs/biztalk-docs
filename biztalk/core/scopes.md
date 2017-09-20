---
title: "Scopes | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "scopes, exception handling"
  - "Scope shape [Orchestration Designer], nesting"
  - "scopes, variables"
  - "scopes, Scope shape [Orchestration Designer]"
  - "Scope shape [Orchestration Designer], exception handling"
  - "scopes, transactions"
  - "scopes, synchronization"
  - "scopes, nesting"
  - "Scope shape [Orchestration Designer], transactions"
ms.assetid: 51d81ce4-0034-4415-b6ab-4c952737c1bd
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Scopes
A scope is a framework for grouping actions. It is primarily used for transactional execution and exception handling.  
  
 A scope contains one or more blocks. It has a body and can optionally have appended to it any number of exception-handling blocks. It may have an optional compensation block as well, depending on the nature of the scope. Some scopes will be purely for exception handling, and will not require compensation. Other scopes will be explicitly transactional, and will always have a default compensation handler, along with an optional compensation handler that you create for it. A transactional scope will also have a default exception handler and any number of additional exception handlers that you create for it.  
  
## Synchronized scopes  
 You can specify that scopes are synchronized or not synchronized. By synchronizing a scope, you ensure that any shared data that is accessed within it will not be written to by one or more parallel actions in your orchestration, nor will it be written to while another action is reading it.  
  
 Atomic transaction scopes are always synchronized. All actions within a synchronized scope are considered synchronized, as are all actions in any of its exception handlers. Actions in the compensation handler for a transactional scope are not synchronized.  
  
> [!CAUTION]
>  Note that you can still run into a deadlock condition if you do not design your processes carefully. For example: two branches of a parallel in orchestration A access the same message, one to send it and one to receive it, so both must have a synchronized scope. A second orchestration receives the message and sends it back. It is possible that the sending branch in orchestration A will receive its locks before the receiving branch, and you will end up with a deadlock.  
  
## Nesting of scopes  
 You can nest **Scope** shapes inside other **Scope** shapes. The rules for nesting scopes are as follows:  
  
-   Transactional and/or synchronized scopes cannot be nested inside synchronized scopes, including the exception handlers of synchronized scopes.  
  
-   Atomic transaction scopes cannot have any other transactional scopes nested inside them.  
  
-   Transactional scopes cannot be nested inside nontransactional scopes or orchestrations.  
  
-   You can nest scopes up to 21 levels deep.  
  
-   **Call Orchestration** shapes can be included inside scopes, but the called orchestrations are treated the same as any other nested transaction, and the same rules apply.  
  
-   **Start Orchestration** shapes can be included inside scopes. Nesting limitations do not apply to started orchestrations.  
  
## Scope variables  
 You can declare variables such as messages and correlation sets at the scope level. You cannot use the same name for a scope variable as for an orchestration variable, however; name hiding is not allowed.  
  
## See Also  
 [Using Transactions and Handling Exceptions](../core/using-transactions-and-handling-exceptions.md)   
 [Atomic Transactions](../core/atomic-transactions.md)