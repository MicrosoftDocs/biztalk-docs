---
description: "Learn more about: Creating the FRR Receive Pipeline"
title: "Creating the FRR Receive Pipeline"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Creating the FRR Receive Pipeline
To perform FIN Response Reconciliation, you must create a receive pipeline that contains the SWIFT FRR Decoder and SWIFT FRR CorrelationSet Resolver pipeline components, in addition to the SWIFT disassembler.  

 **Summary**  

 Create a receive pipeline with the following stages/properties:  

|Stage/Property|Component/Setting|  
|---------------------|------------------------|  
|Disassemble stage|SWIFT Disassembler|  
|BRE Validation property (SWIFT Disassembler)|True|  
|XML Validation property (SWIFT Disassembler)|True|  
|SWIFT Header Schema property (SWIFT Disassembler)|(None)|  
|Decoder stage|SWIFT FRR MQSeries Decoder|  
|Party Resolution stage|SWIFT FRR Correlation Set Resolver|  

### To create a custom receive pipeline for FRR  

1. In Solution Explorer of Visual Studio, right-click the project containing your [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] pipelines, point to **Add**, and then click **New Item**.  

2. In the Add New Item dialog box, click **Pipeline Files** in the Categories pane, and then select **Receive Pipeline** in the Templates pane.  

3. In the **Name** box, type a name for your receive pipeline, such as **FRRReceivePipeline.btp**. Click **Add**.  

   > [!NOTE]
   >  Before you perform step 4, you must have added the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] FRR pipeline components to the toolbox, as described in [Adding SWIFT Pipeline Components to the Toolbox](../../adapters-and-accelerators/accelerator-swift/adding-swift-pipeline-components-to-the-toolbox.md).  

4. In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], click **View** and then click **Toolbox**.  

5. From the BizTalk Pipeline Components Toolbox pane, drag the **SWIFT Disassembler** to the **Drop Here** box below the **Disassemble** stage shape in Pipeline Designer.  

6. With the **SWIFT Disassembler Component** selected in Pipeline Designer, in **Properties**, verify that the **BRE Validation** and **XML Validation** properties are set to **True**, and the **SWIFT Header Schema** property is set to **(None)**.  

7. In the BizTalk Pipeline Components Toolbox, drag **SWIFT FRR MQSeries Decoder** to the **Drop Here** box below the **Decoder** stage shape in Pipeline Designer.  

8. From the BizTalk Pipeline Components Toolbox pane, drag **SWIFT FRR Correlation Set Resolver** to the **Drop Here** box below the **ResolveParty** stage shape in Pipeline Designer.  

9. In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], click **File**, and then click **Save All**.
