---
description: "Learn more about: CICS Components"
title: "CICS Components1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9bd6bb3e-af55-48be-841e-6e7765a0cf32
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# CICS Components
Customer Information Control System (CICS) is a mainframe application system that provides components such as a transaction-processing monitor and a transaction-processing manager for a mainframe computer to run online transaction processing (OLTP) applications. You can install CICS on all three mainframe operating systems: Multiple Virtual Storage (MVS), Virtual Storage Extended (VSE), and Virtual Machine (VM). Due to the popularity of MVS, CICS is commonly installed on MVS mainframe computers. CICS extends the capabilities of a batch-only environment by providing the application system components that allow the mainframe computer to run OLTP applications.  
  
 CICS can run online applications on the mainframe computer because CICS acts almost like a separate operating system: it manages its own memory address space, runs its own file management functions, and manages the concurrent execution of multiple transaction applications.  
  
 To use Transaction Integrator (TI) successfully, you must understand the following CICS components and terminology:  
  
 CICS region  
 Each instance of CICS running on a mainframe computer is defined in Virtual Telecommunications Access Method (VTAM) by using a VTAM application statement. Each CICS instance defined in an application statement is called a CICS region. It is useful to define multiple CICS regions on a single mainframe computer because it allows you to logically group TPs in separate CICS regions and to use at least one CICS region for test purposes.  
  
 TP  
 The transaction program (TP) is the application software that executes under the supervision of CICS and contains the actual programming code necessary to process the business logic. Other terms that refer to a TP are transaction, host transaction program, application program, and program.  
  
 Transaction ID  
 All TPs that run under CICS are invoked by using a unique, four-character transaction identification (TRANID). This may sometimes be confusing because the transaction ID typically is different than the TP name. For example, the TP that handles CICS resource definitions is called Resource Definition Online (RDO), whereas the transaction ID that starts RDO is CEDA.  
  
 Program control table (PCT)  
 The program control table (PCT) is a CICS table that contains a mapping between TRANIDs and their associated TP names. After the TRANID is invoked, CICS starts the TP associated in the PCT with that TRANID.  
  
 File control table (FCT)  
 The file control table (FCT) is a CICS table that monitors which VSAM files are available to TPs. The FCT lists the name and type of VSAM files and valid operations that users can perform on each file. Although CICS can access other types of data stores, such as DB2, it accesses VSAM most frequently.  
  
 RDO  
 The RDO is a CICS TP that allows a CICS systems programmer to define the resources contained in the internal control tables.  
  
 Task  
 A task executes the functions of the TP; every CICS TP performs its functions by using a task. A CICS TP can use a single task or multiple tasks to perform its functions. Each time a TP is invoked, CICS starts the tasks required to perform its functions. CICS is a multitasking environment, which means that more than one task can, and often is, running at the same time.  
  
## See Also  
 [Transaction Integrator Architecture](../core/transaction-integrator-architecture1.md)   
 [Online Transaction Processing](../core/online-transaction-processing2.md)
