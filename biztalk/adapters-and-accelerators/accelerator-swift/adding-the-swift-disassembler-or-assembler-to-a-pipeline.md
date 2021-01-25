---
description: "Learn more about: Adding the SWIFT Disassembler or Assembler to a Pipeline"
title: "Adding the SWIFT Disassembler or Assembler to a Pipeline | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pipelines, adding assembler"
  - "assembler, adding to pipelines"
  - "pipelines, adding disassembler"
  - "disassembler, adding to pipelines"
ms.assetid: f39eb340-fe58-4c8f-b3f2-f7686a245095
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Adding the SWIFT Disassembler or Assembler to a Pipeline
You can use BizTalk Pipeline Designer with Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)][!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] to create custom BizTalk receive and send pipelines. You can use the SWIFT disassembler for the "disassemble" stage in a custom receive pipeline. Similarly, you can use the SWIFT assembler for the "assemble" stage in a custom send pipeline. To invoke the SWIFT disassembler or assembler from the Pipeline Designer toolbox, you drag the disassembler or assembler onto the corresponding pipeline stage on the Pipeline Designer canvas. For step-by-step instructions about invoking the disassembler or assembler, see [Module 3: Adding a Pipeline Project](../../adapters-and-accelerators/accelerator-swift/module-3-adding-a-pipeline-project.md) in the End-to-End Tutorial. For more information about the Pipeline Designer or working with pipeline projects, see BizTalk Server Help.  
  
 By design, the SWIFT disassembler expects the "disassemble" stage to be the *final* stage of the receive pipeline that is invoked. Using any subsequent stages will result in unexpected behavior (such the disassembler not invoking subsequent stages, or the disassembler removing context properties that it had previously populated and promoted before publishing the message to the MessageBox database). Similarly, the SWIFT assembler expects the "assemble" stage to be the *first* stage of the send pipeline. Using any preceding stages may impair dynamic message type discovery by the SWIFT assembler.  
  
 You must manually add the SWIFT disassembler and assembler to the Pipeline Designer toolbox the first time you use them. Step-by-step instructions for doing this are detailed in [Module 3: Adding a Pipeline Project](../../adapters-and-accelerators/accelerator-swift/module-3-adding-a-pipeline-project.md) in the End-to-End Tutorial. The components will continue to appear in the toolbox once you manually add them (until you manually remove them or until you uninstall [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]).  
  
## See Also  
 [Working with the SWIFT Disassembler and Assembler](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)
