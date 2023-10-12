---
description: "Learn more about: Two-Phase Commit Performance Considerations"
title: "Two-Phase Commit Performance Considerations1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Two-Phase Commit Performance Considerations
When a Transaction Integrator (TI) component executes within a transaction, the TI run-time environment sends a message to Microsoft Distributed Transaction Coordinator (DTC) in the COM+ environment, enlisting itself on the transaction as a special type of LU 6.2 resource manager. After TI sends its data buffer to the host and receives the reply, it calls the `SetComplete` method and returns control to COM+. At this point, the client application, or other component driving TI, can perform other work also included in the same transaction. When all resource managers have made their updates and issued `SetComplete`, the transaction's creator (which can be COM+ itself for an Auto-Transaction) sends the `Commit` method to DTC. DTC sends the first-phase (`Prepare`) message to all the resource managers, including the TI run-time environment. TI generates the `Prepare PS Header` defined in the SNA Formats, and sends it to the host. It receives a `RequestCommit` in reply, which indicates that the host updates are valid and can be committed, and passes this information back to DTC. DTC collects the votes from all the resource managers, and if all prepared okay, it force-writes a Commit record to the log and sends the `Committed` message. Again, TI translates this into an `SNA PS Header`, receives the reply, and translates this back to DTC. If everything works as planned, DTC rolls back the transaction and the APPC/LU 6.2 conversation is deallocated.  
  
> [!NOTE]
>  Neither TI nor the AP need be concerned about an APPC or CPI/C SYNCPT verb. The decision to "take a SyncPoint" is made by the transaction creator, is expressed in the semantics of OLE transactions, and involves all participants in the transaction, not just the TI LU 6.2 branches. The role of TI is at a lower level; TI acts as a resource manager to DTC. It translates between the COM interfaces used by DTC, and the SNA protocols understood by the host, to perform the two phases of the protocol and enable DTC to make the Commit decision between phase one and phase two.  
  
 From a performance standpoint, guaranteeing the atomicity of the host updates adds significant, unavoidable overhead. There are two additional round-trip message flows to the host for the two-phase commit (2PC), plus the Windows message flows to enlist, and the transaction logging (forced disk writes) by DTC and on the host. Transactions that do not require a great deal of business logic processing can take twice as long or more to complete when you compare it to the same transaction without 2PC.  
  
 The only time you should configure a TI component to support ACID transactions is when the associated host transaction program (TP) modifies a mission critical resource that must be kept consistent with resources on the Windows operating system. If the TP will not modify any resource for which consistency must be guaranteed, configure the TI component as **Does Not Support Transactions**, so that 2PC is not attempted. Then you are also free to use the TCP/IP protocol. The TCP/IP protocol does not support 2PC.  
  
 TI components should never be configured as **Requires a New Transaction**. This means that you are managing the transaction remotely for the host, and it would incur the overhead of creating a new transaction, enlisting on it, and performing the 2PC exchanges with the host, but the TI method would be a transaction unto itself. It is more efficient to enable CICS and IMS to manage their own transactions. Any updates on the Windows operating system would not be part of that transaction, so they would commit or roll back independently.  
  
> [!NOTE]
>  Additional business logic processing on the same server lowers the throughput limits, stealing some of the CPU. However, the cost can be relatively small in the scope of the overall response time budget.  
  
## See Also  
 [Transaction Integrator Performance Guide](../core/transaction-integrator-performance-guide1.md)
