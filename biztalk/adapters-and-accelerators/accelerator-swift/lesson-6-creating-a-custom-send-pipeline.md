---
title: "Lesson 6: Creating a Custom Send Pipeline | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "custom pipelines"
  - "send pipelines, custom pipelines"
ms.assetid: 73a3a546-1e43-4b93-87d3-9bfb32685a57
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Lesson 6: Creating a Custom Send Pipeline
In this lesson, you create a custom send pipeline using BizTalk Pipeline Designer. A send pipeline is a pipeline you run on messages before [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] sends the messages to their destination.  
  
 You configure the custom pipeline to use the SWIFT assembler (ASM) component. The ASM takes an XML-formatted message and converts or serializes the content into a SWIFT flat file. This conversion is based upon the MT103 schema you created in [Lesson 3: Adding a Custom Receive Pipeline](../../adapters-and-accelerators/accelerator-swift/lesson-3-adding-a-custom-receive-pipeline.md).  
  
### To create a custom send pipeline  
  
1. In Solution Explorer, right-click the **SWIFTPipelines** project, point to **Add**, and then click **New Item**.  
  
2. In the Add New Item-SWIFTPipelines dialog box, verify that **Pipeline Files** is selected in the Categories pane, and then select **Send Pipeline** from the Templates pane.  
  
3. In the **Name** box, type **MT103SendPipeline.btp**.  
  
4. Click **Add** to open the blank pipeline in BizTalk Pipeline Designer.  
  
   > [!NOTE]
   >  An empty pipeline appears in the BizTalk Pipeline Designer. [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] adds the new pipeline to Solution Explorer under the SWIFTPipelines project.  
  
   Proceed to [Lesson 7: Adding the SWIFT Assembler to a Custom Send Pipeline](../../adapters-and-accelerators/accelerator-swift/lesson-7-adding-the-swift-assembler-to-a-custom-send-pipeline.md).