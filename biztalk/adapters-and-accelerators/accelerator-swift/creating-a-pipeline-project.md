---
title: "Creating a Pipeline Project | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b584e3ab-e824-4977-b4ed-4fc197a6cf7a
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Creating a Pipeline Project
To create a pipeline project:  
  
1.  In Visual Studio, create a new BizTalk project.  
  
2.  Add a receive pipeline item and a send pipeline item to the project.  
  
3.  Open the ReceivePipeline.btp file.  
  
4.  In Pipeline Designer, open the Toolbox.  
  
5.  Right-click the **Toolbox** surface, and then select **Choose Items**.  
  
6.  In the Choose Toolbox Items window, click the **Pipeline Components** tab, and then select the following pipeline components:  
  
    -   SwiftMXDisassembler  
  
    -   SwiftMXAssembler  
  
    -   Swift MXRR Encoder Component  
  
    -   Swift MXRR Decoder Component  
  
    -   Swift MXRR Correlation Party Resolver Component  
  
7.  Drag the **SwiftMXDisassembler** component into the Disassembler placeholder in the Receive Pipeline.  
  
8.  In the SwiftMXDisassembler component properties, set the **BRE Validation** property to TRUE or FALSE depending on whether you want to enable Business Rules Validation on the incoming messages. Set the **TransportHeaderRequired** property to TRUE or FALSE depending on whether you want to provide transport header in messages.  
  
9. Drag the Swift MXRR Decoder and Swift MXRR Correlation Party Resolver component into the Decoder and the Party Resolver placeholder inside the Receive Pipeline.  
  
10. Select the **MXRR Correlation Party Resolver** in the pipeline. In the Pipeline Component Properties window, set the **Enable BAM Logging for Reconciliation** property to TRUE or FALSE, depending on whether you want to enable reconciliation for the SWIFT responses.  
  
11. Open the **SendPipeline.btp** file, In the Pipeline Designer, open the **Toolbox**.  
  
12. In Toolbox, drag the **SwiftMXAssembler** component into the Assembler placeholder inside the Send Pipeline.  
  
13. Drag the **Swift MXRR Encoder** component into the Encoder placeholders of the Send Pipeline.  
  
14. Select the **MXRR Encoder Party Resolver** in the pipeline, and then in the Pipeline Component Properties window, set the following properties.  
  
15. Enable **BAM Logging for Reconciliation** to TRUE or FALSE depending on whether you want to enable reconciliation for the SWIFT responses.  
  
16. Set the **LAU Required** to TRUE or FALSE depending on whether you have to enable the signing of the message at the SWIFT Alliance Access (SAA).  
  
17. If the LAU Required property has been has been set to TRUE, then provide LAU Key First Part and LAU Key Second Part (the values have to be the same ones that were provided while configuring the SAA.)  
  
18. Build and then deploy the project.