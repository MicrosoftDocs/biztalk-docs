---
title: "Online Transaction Processing2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4c71c085-0cc7-46f1-8395-99e01376a43a
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Online Transaction Processing
Most mainframe and midrange mission-critical applications run as online transaction processing (OLTP) applications under the direction of a transaction-processing monitor, such as customer information control system (CICS) and information management system (IMS). CICS and IMS are widely used in mainframe environments to create distributed OLTP solutions, such as customer-tracking and order-entry solutions. TI integrates CICS and IMS by creating .NET interfaces to the CICS and IMS transactions and by calling for the services of, or invoking, those transactions on the host from a Windows-based application.  
  
 A two-phase commit (2PC) protocol is used when a transaction involves multiple programs running on multiple computers. Use the 2PC protocol to verify that each computer has completed its part of the transaction.  
  
## In This Section  
 [CICS Components](../core/cics-components1.md)  
  
 [IMS Components](../core/ims-components2.md)  
  
 [Two-Phase Commit](../core/two-phase-commit2.md)  
  
 [Windows Transactions vs. Mainframe Transactions](../core/windows-transactions-vs-mainframe-transactions2.md)  
  
## See Also  
 [Transaction Integrator Architecture](../core/transaction-integrator-architecture1.md)