---
title: "How to Resolve Transactions Manually1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: df22f0ba-a8e6-4444-840a-33c626fde6be
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Resolve Transactions Manually
The following procedures describe how to resolve a transaction manually when it cannot be committed or aborted by the system due to a resynchronization failure following restoration of services between the Windows and IBM LU 6.2 systems. Such resynchronization failures can occur, for example, if CICS makes a heuristic decision to commit or abort a transaction. CICS versions prior to 5 will do this. Typically, TI and Microsoft Distributed Transaction Coordinator (DTC) will automatically resolve all in-doubt transactions when service between the systems is restored. However, if resynchronization and recovery cannot be automatically achieved for any reason, you can resolve transactions manually by using one of the following procedures.  
  
### To resolve a transaction manually  
  
1. For transactions in the **Only Failed Remain to Notify** state or in the **Cannot Notify Committed** state:  
  
    The Only Failed Remain to Notify and the Cannot Notify Committed states indicate that the transaction has committed, but some subordinate Microsoft DTC or IBM LU 6.2 systems have not been notified.  
  
   1.  Start TI Manager, and navigate to **Transaction List** in the console tree's **Component Services** folder in Windows.  
  
   2.  In the **Transaction List** details pane, right-click the transaction that is in the Only Failed Remain to Notify or Cannot Notify Committed state.  
  
        This will display the parent DTC and the subordinate DTC and IBM LU 6.2 systems for the transaction.  
  
   3.  Force the transaction to commit on each subordinate system.  
  
   4.  Return to the DTC that shows the Only Failed Remain to Notify or Cannot Notify Committed state, and force that DTC to forget the transaction.  
  
   > [!CAUTION]
   >  Do not manually forget a transaction until all subordinate systems have been notified of the transaction outcome.  
  
2. For transactions in the **Aborted** state or in the **Cannot Notify Aborted** state:  
  
    The Aborted and Cannot Notify Aborted states indicate that the transaction has aborted. If a transaction remains in one of these states for an extended period of time, this indicates that some subordinate DTC or IBM LU 6.2 systems have not been notified of the transaction's outcome.  
  
   1.  Start TI Manager, and navigate to **Transaction List** in the console tree's **Component Services** folder in Windows.  
  
   2.  In the **Transaction List** details pane, right-click the transaction that is in the Aborted or Cannot Notify Aborted state. This will display the parent DTC and the subordinate DTC and IBM LU 6.2 systems for the transaction.  
  
   3.  Force the transaction to commit on each subordinate system.  
  
   4.  Return to the DTC that shows the **Aborted** or **Cannot Notify Aborted** state, and force that DTC to forget the transaction.  
  
   > [!CAUTION]
   >  Do not manually forget a transaction until all subordinate systems have been notified of the transaction outcome.  
  
   For more information about resolving transactions manually, see the Windows documentation.  
  
> [!NOTE]
>  Resolving a transaction manually does not apply to TCP/IP because the IBM TCP/IP protocol does not currently support ACID (atomic, consistent, isolated, durable) transactions.