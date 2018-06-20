---
title: "Lesson 4: Building and Deploying the Assembly | Microsoft Docs"
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
ms.assetid: 58397c35-6048-4ac9-a8b8-a528dd1cb82a
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Lesson 4: Building and Deploying the Assembly
In this lesson, you build and deploy the project to generate an assembly that contains the schemas you created in the previous lessons. This task ensures there are no compilation errors in the work you created so far.  
  
 Deploying an assembly places a copy of the assembly in the Configuration database and installs it in the global assembly cache (GAC). In the following procedure, you deploy directly from Solution Explorer.  
  
 When the project compiles into an assembly (DLL file), [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] saves the DLL in the \<*drive*\>:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for SWIFT\bin\Development folder within the project folder.  
  
### To build and deploy the project  
  
1. In Solution Explorer, right-click **SWIFTSchemas**, and then click **Build**.  
  
   > [!NOTE]
   >  Verify that **Build Succeeded** appears in the lower left-hand corner of the screen. During the compilation process, you may see some status messages. These messages are normal when dealing with the SWIFT schemas. If any errors appear, click Tools, and then click BizTalk Server Administration to open the BizTalk Server Administration Console. Use the Event Viewer and the Health and Activity Tracking (HAT) feature in the BizTalk Administration Console to correct your errors and rebuild.  
  
2. Using [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, browse to the **\<*drive*\>:\labs\SWIFTProject\SWIFTSchemas\bin\Development** folder, and verify that the **SWIFTSchemas.dll** file exists in this folder.  
  
3. In Solution Explorer, right-click **SWIFTSchemas**, and then click **Deploy**.  
  
   > [!NOTE]
   >  Verify that **Deploy Succeeded** appears in the lower left corner of the screen.  
  
### To confirm deployment success  
  
1. Click **View** and then click **BizTalk Explorer**.  
  
2. Expand the **Assemblies** node and confirm that **SWIFTSchemas (1.0.0.0)** appears in the list.  
  
    If SWIFTSchemas appears in the list, the assembly deployed successfully and can be referenced and used from other [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] projects.  
  
   Proceed to [Module 3: Adding a Pipeline Project](../../adapters-and-accelerators/accelerator-swift/module-3-adding-a-pipeline-project.md).