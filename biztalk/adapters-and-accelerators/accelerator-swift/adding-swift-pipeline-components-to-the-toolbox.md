---
title: "Adding SWIFT Pipeline Components to the Toolbox | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "toolbox, adding pipelines"
  - "pipelines, adding to toolbox"
ms.assetid: 3821c10e-ef9b-4657-b934-cff6d096f654
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Adding SWIFT Pipeline Components to the Toolbox
You must add the SWIFT pipeline components to the [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] Toolbox, so that you can create custom pipelines using these components. This is required to create pipelines for either Message Repair and New Submission or FIN Response Reconciliation.  
  
 **Summary**  
  
 Add the following SWIFT pipeline components to the [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] Toolbox:  
  
-   SWIFT Assembler (for Message Repair and New Submission or FIN Response Reconciliation (FRR))  
  
-   SWIFT Disassembler (for Message Repair and New Submission or FRR)  
  
-   SWIFT Frr Correlation Set Resolver (for FRR)  
  
-   SWIFT Frr MQSeries Decoder (for FRR)  
  
-   SWIFT Frr MQSeries Send Component (for FRR)  
  
### To add A4SWIFT pipeline components to the toolbox  
  
1.  In Visual Studio, on the **Tools** menu, click **Choose Toolbox Items**.  
  
2.  In the **Choose Toolbox Items** dialog box, on the **BizTalk Pipeline Components** tab, select **SWIFT Assembler** and **SWIFT Disassembler**. If you will be using FIN Response Reconciliation, select **SWIFT Frr Correlation Set Resolver**, **SWIFT Frr MQSeries Decoder**, and **SWIFT Frr MQSeries Send Component**.  
  
3.  Click **OK**.