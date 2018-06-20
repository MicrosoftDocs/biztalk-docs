---
title: "Configuring the SWIFT Disassembler | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configuring, disassembler"
  - "disassembler, configuring"
ms.assetid: f3773781-7412-421c-943c-18cc665da8d9
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring the SWIFT Disassembler
The SWIFT disassembler (DASM) performs the following tasks when you invoke it in a [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] receive pipeline:  
  
- Dynamically discovers the message type and resolves the document schema  
  
- Parses SWIFT flat files into XML  
  
- Invokes the XML validating reader to perform XML (schema) validation  
  
- Invokes the Business Rule Engine (BRE) to perform BRE validation  
  
- Publishes a parsed XML message to the MessageBox database with promoted context properties and serialized error collection XML  
  
- Processes inbound batches  
  
  You can configure the functionality listed above to meet the specific requirements for a user scenario and [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] solution.  
  
  BizTalk Pipeline Designer configures the SWIFT disassembler during development time of the custom receive pipeline.  
  
  To configure the SWIFT disassembler after it has been added to the disassemble stage of a custom receive pipeline, select the SWIFT disassembler component on the BizTalk Pipeline Designer canvas. The SWIFT disassembler then receives focus and you can set its configuration properties using the Properties window within [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)][!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)].  
  
  For a table of available configuration properties and their descriptions and usage details, see [SWIFT Disassembler Configuration Properties](../../adapters-and-accelerators/accelerator-swift/swift-disassembler-configuration-properties.md).  
  
  For information about using the SWIFT disassembler for different scenarios and setting the configuration properties, see [Working with the SWIFT Disassembler and Assembler](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md).  
  
  When [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] compiles the custom pipeline binary, it statically writes the configuration settings to the custom pipeline. Therefore, you cannot change configuration properties during deployment or run time.  
  
> [!NOTE]
>  After you configure, compile, and deploy a custom pipeline, changes in the configuration require recompiling and redeployment of the custom pipeline.  
  
 For information about creating, building, and deploying custom pipelines, see BizTalk Server Help.  
  
 This section contains:  
  
-   [SWIFT Disassembler Configuration Properties](../../adapters-and-accelerators/accelerator-swift/swift-disassembler-configuration-properties.md)