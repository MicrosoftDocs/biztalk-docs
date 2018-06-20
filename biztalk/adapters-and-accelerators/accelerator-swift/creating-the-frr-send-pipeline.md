---
title: "Creating the FRR Send Pipeline | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FRR, creating send pipelines"
  - "creating, send pipelines"
  - "send pipelines, creating"
ms.assetid: c6cd2047-ea53-425f-80cc-b02a1deb5292
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Creating the FRR Send Pipeline
To perform FIN Response Reconciliation, you need to create a send pipeline that contains the SWIFTAsmFrrMQSeriesHelper pipeline component, in addition to the SWIFT assembler.  

 **Summary**  

 Create a send pipeline with the following stages:  

|Stage|Component|  
|-----------|---------------|  
|Assemble stage|SWIFT assembler|  
|Encode stage|SWIFT Frr MQSeries Send Component|  

### To create a custom send pipeline for FRR  

1. In Solution Explorer of Visual Studio, right-click your pipeline project, point to **Add**, and then click **New Item**.  

2. In the Add New Item dialog box, select **Send Pipeline** from the Templates pane.  

3. In the **Name** box, type a name for your receive pipeline, such as **FRRSendPipeline.btp**. Click **Add**.  

4. In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], click **View** and then **Toolbox**.  

5. From the BizTalk Pipeline Components Toolbox, drag **SWIFT Assembler** to the **Drop Here** box below the **Assemble** stage shape in **BizTalk Pipeline Designer**.  

6. From the BizTalk Pipeline Components Toolbox, drag **SWIFT Frr MQSeries Send Component** to the **Drop Here** box below the **Encode** stage shape in **BizTalk Pipeline Designer**.  

7. In BizTalk Explorer, right-click your pipeline project, click **Undeploy**, and then click **Yes**.  

   > [!NOTE]
   >  After undeploying and then redeploying your pipeline project, you must reset any send ports or receive locations that use pipelines in the previously deployed project.  

8. In Solution Explorer, right-click your pipeline project, and then click **Build**.  

9. After the build has succeeded, right-click your pipeline project, and then click **Deploy**.
