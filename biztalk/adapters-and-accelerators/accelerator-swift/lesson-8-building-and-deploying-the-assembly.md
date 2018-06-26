---
title: "Lesson 8: Building and Deploying the Assembly | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "building assemblies"
  - "deploying, assemblies"
  - "assemblies, building"
  - "assemblies, deploying"
ms.assetid: 74c9dfbd-8365-4600-8885-a9d9c3490dd5
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Lesson 8: Building and Deploying the Assembly
In this lesson, you build and deploy the pipeline project to generate an assembly that contains the pipelines you created in the previous steps. This lesson ensures there are no compilation errors in the work you have created so far.  
  
 You compile the project into an assembly (DLL) file and save it in the \<*drive*\>:\Program Files\Microsoft BizTalk Accelerator for SWIFT\bin\Development folder.  
  
### To build and deploy the project  
  
1. In Solution Explorer, right-click **SWIFTPipelines**, and then click **Build**.  
  
   > [!NOTE]
   >  During the compilation process, you should not see any failures. If you do, check the source of the error, correct it and then re-build the project. You may, however, see a number of warnings related to the A4SWIFT pipeline components. You can correct the condition leading to these warnings by setting the **Copy Local** properties of the pipeline component references to **False**. For more information, see "Building a pipeline project may result in warnings" in [Miscellaneous Known Issues](http://msdn.microsoft.com/library/bc94c781-2a56-4f80-8ecb-e654de2f6ed6).  
  
2. To verify the creation of the SWIFTPipelines.dll file, using [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, browse to \<*drive*:\>\labs\SWIFTProject\SWIFTPipelines\bin\Development, and ensure that the file exists in this folder.  
  
3. In Solution Explorer, right-click **SWIFTPipelines**, and then click **Deploy**.  
  
   > [!NOTE]
   >  During the deployment process, you should not see any failures or warnings. If you do, check the source of the error, correct it, and then re-deploy the project.  
  
4. To conform deployment success, in the **View** menu of [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], click **BizTalk Explorer**.  
  
5. Right-click **BizTalk Configuration Databases**, and then click **Refresh**.  
  
6. Expand the **Assemblies** node and confirm that the accelerator successfully deployed **SWIFTPipelines (1.0.0.0)**.  
  
   Proceed to [Module 4: Creating XML Receive and Flat File Send Ports](../../adapters-and-accelerators/accelerator-swift/module-4-adding-an-xml-receive-location-and-flat-file-send-port.md).