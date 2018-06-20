---
title: "Lesson 5: Adding the SWIFT Disassembler to a Custom Receive Pipeline | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "receive pipelines, adding disassembler"
  - "custom pipelines"
  - "disassembler, custom pipelines"
  - "disassembler, adding to pipelines"
ms.assetid: 96e26d97-bfab-448f-b7b6-3bc2ec3ccebf
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Lesson 5: Adding the SWIFT Disassembler to a Custom Receive Pipeline
In this lesson, you add the custom SWIFT disassembler (DASM) to your pipeline. A DASM pipeline component is a pipeline component that divides messages in a batch into individual documents.  
  
 The DASM pipeline components provided in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Server are:  
  
- Flat file disassembler  
  
- BizTalk Framework disassembler  
  
- XML disassembler  
  
  [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] adds an additional SWIFT disassembler.  
  
### To add the SWIFT custom disassembler to your pipeline  
  
1. From the View menu, click **Toolbox**.  
  
2. From the **BizTalk Pipeline Components Toolbox**, click **SWIFT Disassembler** and drag it to the **Drop Here** box below the **Disassemble** stage shape in **BizTalk Pipeline Designer**. Leave the **SWIFT Disassembler** shape selected in the **BizTalk Pipeline Designer**.  
  
3. In the **Properties** pane, select **Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.HeaderSchema** for the **SWIFT Header Schema** property.  
  
   > [!NOTE]
   >  Do not confuse **SWIFT Header Schema** and Message Header Schema. You must set **SWIFT Header Schema** in step 3.  
  
4. In the **Properties** pane, ensure that the **BRE Validation** property is set to **True**.  
  
   > [!NOTE]
   >  An explanation of the Business Rule Engine (BRE) follows later in this tutorial.  
  
5. In the **Properties** pane, ensure that the **XML Validation** property is set to **True**.  
  
6. In the **Properties** pane, ensure that the **Inbound Debatching** property is set to **False**.  
  
7. On the **File** menu, select **Save All** to save your changes.  
  
   Proceed to [Lesson 6: Creating a Custom Send Pipeline](../../adapters-and-accelerators/accelerator-swift/lesson-6-creating-a-custom-send-pipeline.md).