---
title: "Mainframe Issues Affecting Transaction Recovery2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3466dd46-a437-4c1c-9a5e-0042fd052146
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Mainframe Issues Affecting Transaction Recovery
In some situations, TI cannot process new transactions with a remote environment. This can be correct behavior. For example, if TI exception 1227 is returned to a client application or logged in an event, and the HRESULT is 8004D110, it indicates that new transactions with this remote environment cannot be accepted because previous transactions were not resolved after a communications failure.  
  
 When the two-phase commit process does not complete, CICS must hold the transaction in the In-Doubt state until communications are re-established. Then TI will perform recovery protocols to ensure that the transaction is in the same state at all nodes. CICS must be configured correctly for this to occur.  
  
 If CICS terminates unexpectedly, and then is restarted in a cold state, there is no memory in its log of any transactions that have not completed. Therefore, these transactions cannot be automatically recovered to a consistent state. Verify that all transactions have completed before stopping CICS, or configure CICS for a warm restart using the same log so that any pending transactions can be recovered.  
  
 CICS Transaction Server allows the administrator to specify a Wait Time in the In-Doubt Attributes of a transaction. Be sure to specify a value that is adequate to allow communications to be re-established in most cases. If this timeout elapses before all transactions left in the In-Doubt state have been recovered, CICS will make a heuristic decision to resolve them locally. If this decision conflicts with the decision made for the transactions by Microsoft DTC (Distributed Transaction Coordinator), new transactions cannot be started until the outcome of the previous transactions have been manually overridden.  
  
 In CICS versions prior to CICS Transaction Server, there is no Wait Time in the Recovery attributes. Assigning the Wait value to the In-Doubt attribute does not cause CICS to place the transaction in the state requested by TI when recovery is attempted. If you are using these versions of CICS, set the In-Doubt attribute to Backout or Commit. If a resulting heuristic decision is incorrect and prevents new transactions from beginning, override the outcome of the transaction using DTC.  
  
 Examine the Windows Event Log for messages from the SNA LU 6.2 Resync TP service indicating that transactions were not recovered successfully. Follow the suggested actions. Use Microsoft Transaction Server's Transaction List window to show pending transactions. Right-click the transaction to show its properties. Resolve it to agree with the state that CICS was configured to select heuristically, or to the backed-out or aborted state if CICS terminated unexpectedly and started up cold. The event in the log identifies the transaction and the state chosen by CICS.  
  
> [!NOTE]
>  This does not apply to TCP/IP because TCP/IP does not support ACID (atomic, consistent, isolated, and durable) transactions.  
  
## See Also  
 [How to Resolve Transactions Manually](../core/how-to-resolve-transactions-manually1.md)