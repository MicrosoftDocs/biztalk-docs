---
title: "Batching Tutorial | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "batching tutorial"
  - "tutorials, batching tutorial"
  - "batching tutorial, about the tutorial"
  - "batching, tutorial"
ms.assetid: e9010638-74cf-47cd-8cc9-9d6fd08a1b8d
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Batching Tutorial
This tutorial provides step-by-step procedures for using [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] to receive and send batched messages. Batching involves receiving and/or sending a group of individual messages (or acknowledgments) as a single composite message.  
  
 BTAHL7 supports the following three message batching scenarios:  
  
- **Fragmented inbound batch**. In this scenario, BTAHL7 receives an HL7 message batch, and then routes the individual messages to the destination system.  
  
- **Batch in/batch out**. BTAHL7 receives an HL7 message batch, verifies the individual messages within the batch, and then routes the message batch to the destination system.  
  
- **Create batch (or outbound batching)**. BTAHL7 receives individual messages and batches them before routing them to the destination system.  
  
  This tutorial includes parts for each of the three batching scenarios. Use the three parts of the tutorial in the order provided; part 1 contains prerequisite steps for part 2 and part 3.  
  
## In This Section  
  
-   [Preparing to Use the Batching Tutorial](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-batching-tutorial.md)  
  
-   [Part 1: Fragmented Inbound Batch Scenario](../../adapters-and-accelerators/accelerator-hl7/part-1-fragmented-inbound-batch-scenario.md)  
  
-   [Part 2: Batch In/Batch Out Scenario](../../adapters-and-accelerators/accelerator-hl7/part-2-batch-in-batch-out-scenario.md)  
  
-   [Part 3: Create-Batch Scenario](../../adapters-and-accelerators/accelerator-hl7/part-3-create-batch-scenario.md)