---
title: "Lesson 2: Adding Project References | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "references [projects]"
  - "projects, adding references"
ms.assetid: ddc2bf49-cddd-4edb-8043-870897879655
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Lesson 2: Adding Project References
You add project references so your pipelines can access the default runtime schemas located in the Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.dll file. This assembly file contains the header schema with promoted properties required for message-type resolution.  
  
 You reference the header schemas later when you add the disassembly component to the receive pipeline.  
  
### To add a reference to the default SWIFT RuntimeSchemas assembly  
  
1.  In Solution Explorer, ensure that the **SWIFTPipelines** project is expanded. Right-click **References**, and then click **Add Reference**.  
  
2.  In the Add Reference dialog box, click the **Browse** tab.  
  
3.  Browse to **\<*drive*\>:\Program Files\Microsoft BizTalk Accelerator for SWIFT\Assemblies**.  
  
4.  Select the **Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.dll** file.  
  
5.  Click **Add**, and then click **OK**.  
  
    > [!NOTE]
    >  The RuntimeSchemas assembly (dll) that you selected now appears in the references collection in the SWIFTPipelines project.  
  
#### To add a reference to the SWIFTPipelines schemas assembly  
  
1. In Solution Explorer, under the **SWIFTPipelines** project, right-click **References**, and then click **Add Reference**.  
  
2. In the Add Reference dialog box, on the **Projects** tab, click the **SWIFTSchemas** project, click **Add**, and then click **OK**.  
  
3. On the **File** menu, click **Save All** to save your changes.  
  
   Proceed to [Lesson 3: Adding a Custom Receive Pipeline](../../adapters-and-accelerators/accelerator-swift/lesson-3-adding-a-custom-receive-pipeline.md).