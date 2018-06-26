---
title: "IMS Components2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1b237458-0338-4560-93cd-ed19f59e7722
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# IMS Components
The information management system (IMS) provides a transaction program (TP) Monitor with an integrated TP Manager and hierarchical database. Both the TP Monitor and the database can coordinate transactions with non-IMS TP Monitors and databases.  
  
 To use Transaction Integrator (TI) successfully, you must understand the following IMS components and terminology:  
  
 IMS region  
 IMS uses defined regions to perform its functions. The following regions are typically defined in VTAM when using IMS:  
  
- Control region - The main IMS region. It owns all of the databases that IMS transactions access and is responsible for all communications with the databases. It runs continuously and oversees the operation of other dependent regions.  
  
- Message processing region (MPR) - A dependent region used for processing messages. The control region schedules TPs to run in the MPR. You can have multiple MPRs defined on a single mainframe computer.  
  
- Batch message processing (BMP) region - A dependent region used for processing batch operations.  
  
  IMS message queue  
  The IMS message queue is used by TPs to access the MPP region for processing. Each MPP region has an IMS message queue associated with it. Placing application data in the IMS message queue allows the IMS server TP to use standard Get Unique (GU), Get Next (GN), and Insert (ISRT) calls to exchange data with a client application.  
  
  Data Language (DL)/I  
  Data language (DL)/I is the programming language used in traditional IMS environments to access IMS databases. IMS TPs and CICS TPs can be written in many different programming languages, such as COBOL, PL/I, C, VS Pascal, Ada, REXX, or assembler language. However, when any of these TPs needs to access IMS databases, they must use the proper DL/I calls from their application code. Some of the standard DL/I calls are:  
  
- GU. This call retrieves input data to be processed.  
  
- GN. This call retrieves sequential records.  
  
- ISRT. This call inserts data into a database or returns data to an invoking client.  
  
## See Also  
 [Transaction Integrator Architecture](../core/transaction-integrator-architecture1.md)   
 [Online Transaction Processing](../core/online-transaction-processing2.md)