---
title: "Long-Running Transactions | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "long-running transactions, about long-running transactions"
  - "atomic transactions, long-running transactions"
  - "long-running transactions, orchestrations"
  - "long-running transactions, nesting"
  - "scopes, examples"
  - "orchestrations, transactions"
  - "compensations, long-running transactions"
  - "compensations, customizing"
  - "transactions, long-running"
  - "transactions, compensation blocks"
  - "long-running transactions"
  - "long-running transactions, timeouts"
  - "compensations, examples"
  - "fault tolerance, long-running transactions"
  - "transactions, examples"
  - "orchestrations, long-running transactions"
  - "transactions, atomic"
  - "transactions, fault tolerance"
  - "scopes, long-running transactions"
  - "long-running transactions, fault tolerance"
  - "transactions, nesting"
  - "examples, scopes"
ms.assetid: 4bf4d0c8-903a-411f-963b-bd4cfdfc2958
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Long-Running Transactions
Long-running transactions are important, commonly used constructs in BizTalk orchestrations. They provide you with facilities for custom scope-based compensation, custom scope-based exception handling, and the ability to nest transactions, all of which give you great flexibility in designing robust transaction architecture.  
  
 You use a long-running transaction when the transaction might need to run for an extended time and you do not need full ACID properties (that is, you do not need to guarantee isolation of data from other transactions). A long-running transaction might have long periods of inactivity, often due to waiting for external messages to arrive.  
  
 Long-running transactions possess consistency, and durability, but not atomicity and isolation. The data within a long-running transaction is not locked; other processes or applications can modify it. The isolation property for state updates is not maintained because holding locks for a long duration is impractical.  
  
 Commitment of a long-running transaction is different than commitment of an atomic transaction. There is no implicit assumption of distributed coordination regarding the outcome (a long-running transaction exists only within a single orchestration instance). Instead, a long-running transaction is considered committed when the last statement in it has completed. There is no "auto" rollback of state in case of a transaction abort. You can achieve this programmatically through the exception and compensation handlers.  
  
 A scope can define its own state by declaring variables, messages, and .NET components. A long-running transaction has access to the state information of its own scope, any scope that encloses it, and any state information that is globally defined within the orchestration. It does not have access to the state information of any scopes that do not enclose it.  
  
## Nesting  
 Long-running transactions can contain atomic transactions or other long-running transactions. They can be nested to arbitrary depths. For example, your transaction might contain two other long-running transactions, each of which might contain atomic transactions.  
  
 Nesting is particularly useful when one or more components of the overall transaction need to be atomic while the overall transaction needs to be long-running. Consider the example of receiving and fulfilling a purchase order. The purchase order can arrive at any time, and the various steps in fulfilling the order might take time to occur, but you still want to treat the entire process as a transaction. The overall transaction in this case clearly needs to be long-running, but an individual step, such as acknowledging a payment, might need to be atomic.  
  
> [!NOTE]
>  You cannot nest a transactional scope within a scope or orchestration that is not transactional. An enclosing scope or orchestration that is not transactional will not manage state, as it must to properly handle the state management of any scopes within it.  
  
> [!NOTE]
>  A synchronized transaction cannot include any other transactions or synchronized scopes.  
  
## Compensation  
 A long-running transaction can specify a compensation block that will be called to compensate for the transaction's activities, after it commits. It might simply undo the transaction where feasible, or perform some other function, such as notification, that helps mitigate the effects of the transaction in some way. If you do not add your own compensation code, the runtime engine will by default call the compensation blocks of the inner transactions, both long-running and atomic, in reverse order, starting with the last transaction committed and finishing with the first transaction committed.  
  
> [!NOTE]
>  Compensation can only be done on a transaction that has committed successfully.  
  
## Fault tolerance  
 Transactions support fault tolerance for recovery from both internal faults (such as machine failures and software faults) and external faults (such as cancel messages). Partial updates within long-running transactions are not rolled back automatically when a transaction failure occurs, as they are in ACID transactions.  
  
 The exception code block for the long-running transaction is called when a fault occurs. The exception code block contains a set of fault handlers that you write to deal with any of the faults that can arise during the execution of the transaction. You can rely on the last known state of the messages, variables, and objects in handling the fault.  
  
 You will typically want your exception handler to evaluate the state of the orchestration at the time the exception occurs, take any necessary action based on that state, and call the compensations of any nested transactions.  
  
 The execution of the long-running transaction is interrupted when a fault occurs. It cannot be resumed after a fault occurs.  
  
## See Also  
 [Scenarios Using Long-Running Transactions](../core/scenarios-using-long-running-transactions.md)   
 [Atomic Transactions](../core/atomic-transactions.md)   
 [Using Transactions and Handling Exceptions](../core/using-transactions-and-handling-exceptions.md)