---
title: "WIP Programming Model2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 29ec253a-759d-414a-a9a3-ef43d8bff039
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# WIP Programming Model
The programming models provide a synchronous bridge between the component object model (COM) or the .NET Framework and the mainframe transaction-programming model. Consequently, Transaction Integrator (TI) has no APIs that a developer must use.  
  
 Although TI uses existing mainframe programming models, you may need to make some changes to an existing mainframe transaction program (TP) if any of the following are true:  
  
- The TP uses a conversational or pseudo-conversational mode. TI supports only the nonconversational TP model known as the ping-pong or request-reply conversational sequence in conversations between clients and servers. The TI programming model requires nonconversational method calls; that is, a single input message and a single output message. See "Supported Conversational Model" for more information.  
  
- The TP has terminal processing logic embedded in the same program with the business logic. To get this program to work with TI, you must first restructure it as two separate TPs, one for the terminal processing logic and the other for the business logic. Then you can use TI with the business logic TP.  
  
- A CICS Link transaction program (TP) using LU 6.2 uses explicit EXEC SYNCPOINT commands. There may be a way to work around this issue without rewriting the TP. For more information, see **TPs with Explicit SYNCPOINT Commands**.  
  
  The topics in this section give you the details on the mainframe programming models and how they are addressed in the TI programming model.  
  
## In This Section  
 [Supported Conversational Model](../core/supported-conversational-model1.md)  
  
 [TPs with Explicit SYNCPOINT Commands](../core/tps-with-explicit-syncpoint-commands2.md)  
  
 [Support for Transactions and Two-Phase Commit](../core/support-for-transactions-and-two-phase-commit2.md)  
  
## See Also  
 [Windows-Initiated Processing](../core/windows-initiated-processing2.md)