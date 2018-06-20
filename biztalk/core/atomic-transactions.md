---
title: "Atomic Transactions | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "atomic transactions"
  - "scopes, examples"
  - "transactions, orchestrations"
  - "orchestrations, transactions"
  - "transactions, isolation levels"
  - "transactions, ACID concept"
  - "transactions, examples"
  - "transactions, atomic"
  - "scopes, transactions"
  - "scopes"
ms.assetid: 5030e1fd-943f-42bc-9296-4f315bd5f733
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Atomic Transactions
BizTalk orchestrations can be designed to run discrete pieces of work, following the classic 'ACID' concept of a transaction. These discrete or atomic units of work, when performed, move the business process from one consistent state to a new, consistent and durable state that is isolated from other units of work. This is typically done by using the **Scope** construct that encapsulates the units of work with the transactional semantics. The entire orchestration can also be defined as an atomic transaction without the use of scopes. The scopes, however, cannot be marked as transactional unless the orchestration itself is marked as a long running or atomic transaction type. Atomic transactions guarantee that any partial updates are rolled back automatically in the event of a failure during the transactional update, and that the effects of the transaction are erased (except for the effects of any .NET calls that are made in the transaction). Atomic transactions in BizTalk orchestrations are similar to distributed transaction coordinator (DTC) transactions in that they are generally short-lived and have the four "ACID" attributes (atomicity, consistency, isolation, and durability):  
  
- **Atomicity**  
  
   A transaction represents an atomic unit of work. Either all modifications within a transaction are performed, or none of the modifications are performed.  
  
- **Consistency**  
  
   When committed, a transaction must preserve the integrity of the data within the system. If a transaction performs a data modification on a database that was internally consistent before the transaction started, the database must still be internally consistent when the transaction is committed. Ensuring this property is largely the responsibility of the application developer.  
  
- **Isolation**  
  
   Modifications made by concurrent transactions must be isolated from the modifications made by other concurrent transactions. Isolated transactions that run concurrently perform modifications that preserve internal database consistency exactly as they would if the transactions were run serially.  
  
- **Durability**  
  
   After a transaction is committed, all modifications are permanently in place in the system by default. The modifications persist even if a system failure occurs.  
  
  The following isolation levels are supported by the atomic transactions used in BizTalk Orchestrations:  
  
- **Read Committed**  
  
   Shared locks are held while the data is being read to avoid dirty reads, but the data can be changed before the end of the transaction, resulting in non-repeatable reads or phantom data.  
  
- **Repeatable Read**  
  
   Locks are placed on all data that is used in a query, preventing other users from updating the data. This prevents non-repeatable reads, but phantom rows are still possible.  
  
- **Serializable**  
  
   A range lock is placed preventing other users from updating or inserting rows into the database until the transaction is complete.  
  
  BizTalk Server ensures that state changes within an atomic transaction—such as modifications to variables, messages, and objects—are visible outside the scope of the atomic transaction only upon commitment of the transaction. The intermediate state changes are isolated from other parts of an orchestration.  
  
> [!NOTE]
>  If an atomic transaction contains a **Receive** shape, a **Send** shape, or a **Start Orchestration** shape, the corresponding actions will not take place until the transaction has committed.  
  
 If you require full ACID properties on the data—for example, when the data must be isolated from other transactions—you must use atomic transactions exclusively.  
  
 When an atomic transaction fails, all states are reset as if the orchestration instance never entered the scope. The rule BizTalk has for atomic transactions is that all variables (not just local to the scope) participate in the transaction. All non-serializable variables and messages used in an atomic transaction should be declared local to the scope; otherwise, the compiler will give the "variable….is not marked as serializable" error. All atomic scopes are assumed to be "synchronized" and the orchestration compiler will provide a warning for redundant usage, if indeed the synchronized keyword is used for atomic scopes. The synchronization for the shared data extends from the beginning of the scope until the successful completion of the scope (including the state persistence at the end of the scope) or to the completion of the exception handler (in case of errors). The synchronization domain does not extend to the compensation handler.  
  
 Atomic transactions can be associated with timeout values at which point the orchestration will stop the transaction and the instance will be suspended. If an atomic transaction contains a Receive shape, a Send shape, or a Start Orchestration shape, the corresponding actions will not take place until the transaction has committed.  
  
 An atomic transaction retries when the user deliberately throws a **RetryTransactionException** or if a **PersistenceException** is raised at the time that the atomic transaction tries to commit. The latter could happen if for instance, the atomic transaction was part of a distributed DTC transaction and some other participant in that transaction stopped the transaction. Likewise, if there were database connectivity problems at the time when the transaction was trying to commit, there would also be a **PersistenceException** raised. If this happens for an atomic scope that has **Retry=True**, then it will retry up to 21 times. The delay between each retry is two seconds by default (but that is modifiable). After 21 retries are exhausted, if the transaction is still unable to commit, the whole orchestration instance is suspended. It can be manually resumed and it will start over again, with a fresh counter, from the beginning of the offending atomic scope.  
  
> [!NOTE]
>  Only the **RetryTransactionException** and **PersistenceException** can cause an atomic scope to retry. Any other exception raised in an atomic scope cannot cause it to retry, even if the **Retry** property is set to **True**. The two-second default delay between each two consecutive retries can be overridden by using a public property on **RetryTransactionException** (if that is the exception that is being used to cause the retries).  
  
 The atomic scopes have restrictions on nesting other transactions that cannot nest other transactions or include **Catch - Exception** blocks.  
  
## DTC transactions  
 While atomic transactions behave like DTC transactions, they are not explicitly DTC transactions by default. You can explicitly make them DTC transactions, provided that any objects being used in the transaction are COM+ objects derived from System.EnterpriseServices.ServicedComponents, and that isolation levels agree between transaction components.  
  
> [!NOTE]
>  An atomic transaction cannot contain any other transactions within it, nor can it contain exception handlers.  
  
> [!NOTE]
>  An atomic transaction cannot contain matching send and receive actions—that is, a request-response pair or a send and receive that use the same correlation set.  
  
## Non-serializable objects  
 If you want to use a non-serializable object within an orchestration, you must use it only within an atomic transaction. Any use of such an object outside of an atomic transaction risks data loss whenever the orchestration is persisted by the engine.  
  
> [!CAUTION]
>  Each Atomic scope represents a persistence point and what that means is the state of the orchestration is saved to the database at each persistence point. Extensive use of Atomic scope will increase the latency in the orchestration. Instead of using Atomic scope for the purpose of creating non-serializable objects, you can use Static method calls which they don not require Atomic scopes, thus eliminating the need for the persistence points.  
  
## See Also  
 [Scenarios Using Atomic Transactions](../core/scenarios-using-atomic-transactions.md)   
 [Long-Running Transactions](../core/long-running-transactions.md)