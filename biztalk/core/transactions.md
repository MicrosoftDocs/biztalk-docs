---
description: "Learn more about: Transactions"
title: "Transactions"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Transactions
The BizTalk Server Orchestration Engine manages the state, applies business logic, and invokes the supporting applications of complex processes and/or transaction sets.  
  
 Business processes can be composed as discrete pieces of work using atomic transactions that automatically roll back all changes in case of errors or long running, which can contain nested transactions and use custom exception handling to recover from error scenarios. These transactional semantics are typically managed through the Scope construct in the Orchestration Designer.  
  
 The long running processes can span days, weeks, and longer time durations. The long running processes typically utilize correlation to correlate messages that are received to the messages that may be sent. The orchestration engine typically dehydrates these instances to conserve system resources and re-hydrates the process upon receipt of these correlated messages. The orchestration engine persists the orchestration state to the MessageBox database at known checkpoints to recover from any application or system exceptions.  
  
 The transactional programming model provided for the BizTalk Orchestration engine includes support for exception handling and recovery from failed transactions, atomic transactions that automatically roll back their actions if an error occurs, or long-running transactions that can contain other transactions as well as custom exception handling.  
  
## In This Section  
  
-   [Atomic Transactions](../core/atomic-transactions.md)  
  
-   [Scenarios Using Atomic Transactions](../core/scenarios-using-atomic-transactions.md)  
  
-   [Long-Running Transactions](../core/long-running-transactions.md)  
  
-   [Scenarios Using Long-Running Transactions](../core/scenarios-using-long-running-transactions.md)  
  
-   [Persistence in Orchestrations](../core/persistence-in-orchestrations.md)
