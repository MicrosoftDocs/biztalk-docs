---
title: "Configuring the SWIFT Assembler | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "assembler, configuring"
  - "configuring, assembler"
ms.assetid: 76944226-e29b-4a7f-a4ab-3c3d5f13ec51
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring the SWIFT Assembler
The SWIFT assembler performs the following tasks when you invoke it in a [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] send pipeline:  
  
- Dynamically discovers the message type and resolves the document schema  
  
- Serializes parsed XML into SWIFT flat files  
  
  You can configure the encoding character set used for encoding the serialized output (for example, to use ASCII or Unicode encoding).  
  
  You configure the SWIFT assembler during development time of the custom send pipeline that uses the SWIFT assembler.  
  
  BizTalk Pipeline Designer configures the SWIFT assembler during development time of the custom send pipeline.  
  
  To configure the SWIFT assembler after it has been added to the assemble stage of a custom send pipeline, select the SWIFT assembler component on the Pipeline Designer canvas. The SWIFT assembler then receives focus, and you can set its configuration properties using the Properties window within [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)][!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)].  
  
  For a table of available configuration properties and their descriptions and usage details, see [SWIFT Assembler Configuration Properties](../../adapters-and-accelerators/accelerator-swift/swift-assembler-configuration-properties.md).  
  
  For information about using the SWIFT assembler for different scenarios and setting the configuration properties, see [Working with the SWIFT Disassembler and Assembler](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md).  
  
  When the custom pipeline binary is compiled, it statically writes the configuration settings to the custom pipeline. Therefore, you cannot change configuration properties during deployment or run time.  
  
> [!NOTE]
>  After you configure, compile, and deploy a custom pipeline, changes in the configuration require recompiling and redeployment of the custom pipeline.  
  
 For information about creating, building, and deploying custom pipelines, see BizTalk Server Help.  
  
 This section contains:  
  
-   [SWIFT Assembler Configuration Properties](../../adapters-and-accelerators/accelerator-swift/swift-assembler-configuration-properties.md)