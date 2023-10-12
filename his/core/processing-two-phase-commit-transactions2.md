---
description: "Learn more about: Processing Two-Phase Commit Transactions"
title: "Processing Two-Phase Commit Transactions2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Processing Two-Phase Commit Transactions
This topic discusses what happens with the two-phase commit (2PC) transaction while it is being processed by Microsoft Distributed Transaction Coordinator (DTC) in COM+, Transaction Integrator (TI), and CICS.  
  
 The process begins when the client application invokes a method on the .NET application that contains the TI object. .NET then allocates a thread for the transaction from its user thread pool, begins the transaction, and passes the method's input parameters to the TI run-time environment. This thread is blocked for the transaction until the response comes back from the CICS host. This is the unit of work time, which consists mostly of time it takes the CICS application to process the transactions business logic and gain access to the database as needed (assuming that the transmission speeds keep up with the LAN speed). When the method's output parameters are sent back to .NET from the host, the commit message is sent to DTC.  
  
 DTC activates the prepare phase for the transactions, causing TI to allocate a thread from its 2PC thread pool and keep it blocked until the request commit message arrives from the host. After all the forks of the transactions are prepared, DTC sends a commit complete message to .NET, then sends the method's output parameters and return values back to the calling client application and releases the thread.  
  
 This completes the transaction for the user, but the transaction monitors (DTC and CICS) still must complete the second phase of the commit, and again, a thread from the TI 2PC thread pool is allocated for each transaction doing the second phase of the commit.  
  
## See Also  
 [Transaction Programs that Run for a Long Time](../core/transaction-programs-that-run-for-a-long-time2.md)   
 [Transaction Integrator Performance Guide](../core/transaction-integrator-performance-guide1.md)
