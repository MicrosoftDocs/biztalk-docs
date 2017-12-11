---
title: "Online Transaction Processing1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 92615b28-6863-4d93-9cc3-50ba6d3a3845
caps.latest.revision: 3
---
# Online Transaction Processing
Most mainframe and midrange mission-critical applications run as online transaction processing (OLTP) applications underthe direction of a transaction-processing monitor, such as customer information control system (CICS) and information management system (IMS). CICS and IMS are widely used in mainframe environments to create distributed OLTP solutions, such as customer-tracking and order-entry solutions. TI integrates CICS and IMS with COM by creating COM and .NET interfaces to the CICS and IMS transactions and by calling for the services of, or invoking, those transactions on the host from a Windows-based application.  
  
 A two-phase commit (2PC) protocol is used when a transaction involves multiple programs running on multiple computers. Use the 2PC protocol to verify that eachl computer has completed its part of the transaction.  
  
## In This Section  
 [CICS Components](../HIS2010/cics-components2.md)  
  
 [IMS Components](../HIS2010/ims-components1.md)  
  
 [Two-Phase Commit](../HIS2010/two-phase-commit1.md)  
  
 [Windows Transactions vs. Mainframe Transactions](../HIS2010/windows-transactions-vs-mainframe-transactions1.md)  
  
## See Also  
 [Transaction Integrator Architecture](../HIS2010/transaction-integrator-architecture2.md)