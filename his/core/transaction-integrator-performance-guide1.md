---
title: "Transaction Integrator Performance Guide1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cc9a4c31-82e0-4724-9f0b-01ad9dffac2a
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Transaction Integrator Performance Guide
To ensure excellent performance out of the box, Microsoft has run performance tests on Transaction Integrator (TI) to determine its performance and scalability in various deployment situations. This section discusses what was learned about TI.  
  
 Many factors can affect performance:  
  
- Security.  
  
- Whether you are using two-phase commit.  
  
- Sharing the server with other Microsoft BackOffice applications.  
  
- Sizing the server initially.  
  
- Planning for future growth.  
  
  This section will help you handle various load conditions and help you tune your system to give the best possible TI performance while avoiding performance pitfalls, especially with transactions that run for a long time.  
  
## In This Section  
 [Major Elements Affecting Overall Performance](../core/major-elements-affecting-overall-performance1.md)  
  
 [Performance Monitoring Counters](../core/performance-monitoring-counters2.md)  
  
 [SNA Communication Tuning](../core/sna-communication-tuning2.md)  
  
 [SNA vs. TCP/IP](../core/sna-vs-tcp-ip1.md)  
  
 [System Sizing](../core/system-sizing1.md)  
  
 [Load Balancing and Hot Backup](../core/load-balancing-and-hot-backup2.md)  
  
 [Security Implications](../core/security-implications1.md)  
  
 [Transaction Size vs. Transaction Throughput](../core/transaction-size-vs-transaction-throughput2.md)  
  
 [Transaction Programs that Run for a Long Time](../core/transaction-programs-that-run-for-a-long-time2.md)  
  
 [Two-Phase Commit Performance Considerations](../core/two-phase-commit-performance-considerations1.md)  
  
 [Data Conversion Cost](../core/data-conversion-cost1.md)  
  
 [ADO Recordsets vs. User-Defined Types in Structured Data Tests](../core/ado-recordsets-vs-user-defined-types-in-structured-data-tests2.md)  
  
 [Remote Environment Selection with the SelectionHint Property](../core/remote-environment-selection-with-the-selectionhint-property2.md)