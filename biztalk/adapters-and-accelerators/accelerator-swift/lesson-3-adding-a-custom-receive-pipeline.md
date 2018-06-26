---
title: "Lesson 3: Adding a Custom Receive Pipeline | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "receive locations, creating custom pipelines"
  - "custom pipelines"
ms.assetid: 1917b8e2-4f1c-4c20-abe4-ea18a406eeeb
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Lesson 3: Adding a Custom Receive Pipeline
In this lesson you create a custom receive pipeline using BizTalk Pipeline Designer. A custom receive pipeline is a pipeline that is run on messages after the adapter receives the messages, but before [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] publishes them to the MessageBox database.  
  
 You configure the custom pipeline to use the SWIFT disassembler (DASM) component. The SWIFT disassembler takes a SWIFT-formatted flat file and converts, or parses, the content of the SWIFT message into an XML-based representation, which [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] can consume.  
  
 The MT103 runtime schema that you added in the previous step ([Lesson 2: Adding Project References](../../adapters-and-accelerators/accelerator-swift/lesson-2-adding-project-references.md)) is the format that you use for the conversion.  
  
### To create a new custom receive pipeline  
  
1. In Solution Explorer, right-click the **SWIFTPipelines** project, point to **Add**, and then click **New Item**.  
  
2. In the Add New Item-SWIFTPipelines dialog box, click **Pipeline Files** in the Categories pane, and then select **Receive Pipeline** from the Templates pane.  
  
3. In the **Name** box, type **MT103ReceivePipeline.btp**.  
  
4. Click **Add** to open the blank pipeline in BizTalk Pipeline Designer.  
  
   An empty pipeline appears in the BizTalk Pipeline Designer. Visual Studio also adds the new pipeline to Solution Explorer under the SWIFTPipelines project.  
  
   Proceed to [Lesson 4: Adding the SWIFT Assembler and Disassembler to the Toolbox](../../adapters-and-accelerators/accelerator-swift/lesson-4-adding-the-swift-assembler-and-disassembler-to-the-toolbox.md).