---
title: "Windows Transactions vs. Mainframe Transactions2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b78b5240-d421-4dc8-ba2e-9fac3316bfaa
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Windows Transactions vs. Mainframe Transactions
In the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Help, a transaction in the Microsoft Windows .NET Framework environment does not mean the same thing as a transaction in the mainframe environment.  
  
- A transaction in the Windows environment is a set of actions coordinated by the Microsoft Distributed Transaction Coordinator (DTC) as an atomic unit of work that meets the ACID test; in other words, a transaction is **a**tomic, **c**onsistent, **i**solated, and **d**urable. Either all the actions in the transaction are completed, or none of them are completed.  
  
- A transaction in the mainframe host (CICS or IMS) environment is a section of code in a structured transaction program (TP), and a TP is a single COBOL program file that contains one or more mainframe transactions. Therefore, a mainframe transaction may or may not meet the ACID test.  
  
  A TI Automation server is a TI component deployed in a .NET Framework application. A single method in a TI Automation server invokes a single mainframe-based TP. Any TI method in the TI Automation server can invoke any transaction in the TP, but it is the TP that determines which of its transactions to run. The mainframe TP makes this decision based on the information sent to it from the TI Automation server. A CICS or IMS TP can provide any type of service, such as terminal interaction, data transfer, database query, and database updates. A TP can also contain one or more transactions.  
  
  A mainframe TP also has a specialized meaning in the IBM CICS environment. Any program that uses Advanced Program-to-Program Communications (APPC) with another program is referred to as a transaction program (TP). APPC is a set of protocols developed by IBM specifically for peer-to-peer networking among mainframes, AS/400s, 3174 cluster controllers, and other intelligent devices. For a TP to communicate directly with another TP using APPC, the two programs must first establish an LU 6.2 session and conversation with each other.  
  
  LU 6.2 is the de facto standard protocol for distributed transaction processing in the mainframe environment. It is used by both CICS and IMS subsystems. One program can interact with another program at one of three levels of synchronization:  
  
- Sync Level 0 has no message integrity beyond sequence numbers to detect lost or duplicate messages.  
  
- Sync Level 1 supports the CONFIRM-CONFIRMED verbs that allow end-to-end acknowledgment for client and server.  
  
- Sync Level 2 supports the SYNCPT verb that provides ACID (atomicity, consistency, isolation, durability) properties across distributed transactions by way of two-phase commit (2PC).  
  
  Of the three sync levels, only Sync Level 2 provides the same guarantees provided by a Windows, COM, COM+, or .NET Framework transaction.  
  
> [!NOTE]
>  The TCP/IP protocol is not designed for distributed transaction processing, so TCP/IP does not provide the ACID guarantee that 2PC in LU 6.2 Sync Level 2 provides. Therefore, it is the network protocol (LU 6.2 or TCP/IP) that determines whether it is possible to guarantee that a transaction in a TP operates as an atomic, consistent, isolated, and durable unit.  
  
 Thus, in the CICS and IMS environment, the term transaction program (TP) may or may not imply the use of 2PC. The term transaction program refers to the program itself. It is only when the term transaction is qualified by adding the term Sync Level 2 that the Windows developer and the mainframe developer can be sure they are referring to the same thing.  
  
 TI supports both Sync Level 0 and Sync Level 2 conversations over LU 6.2 in SNA networks. If a method invocation is part of a DTC-coordinated transaction, TI uses Sync Level 2 to communicate with CICS or IMS version 6.0 with Resource Recovery Services (RRS). If a method invocation is not part of a DTC-coordinated transaction, then TI uses Sync Level 0.  
  
## See Also  
 [Support for Transactions and Two-Phase Commit](../core/support-for-transactions-and-two-phase-commit2.md)   
 [Online Transaction Processing](../core/online-transaction-processing2.md)