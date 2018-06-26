---
title: "Lesson 2: Creating a Strong-Named BizTalk Assembly for the SWIFTSchemas Project | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "assemblies, creating strong-names"
  - "strong-named assemblies"
ms.assetid: 2aacbf38-8b1d-46ea-89ae-5207327bedc1
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Lesson 2: Creating a Strong-Named BizTalk Assembly for the SWIFTSchemas Project
In this lesson, you create a strong name upon which the BizTalk assemblies are compiled and deployed. A strong-named assembly provides several security benefits:  
  
- A strong name guarantees the uniqueness of the assembly by assigning a digital signature and a unique key pair.  
  
- A strong name protects the lineage of the assembly by ensuring that no one else can generate a subsequent version of the assembly.  
  
- A strong name provides a strong integrity check to guarantee that the contents of the assembly have not changed since the last build.  
  
  You can generate a key file by using the strong name tool (sn.exe) that comes with [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)][!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] or the [!INCLUDE[btsDotNetFramework](../../includes/btsdotnetframework-md.md)].  
  
### To create a strong-named BizTalk assembly  
  
1. Start Visual Studio command prompt.  
  
2. At the Visual Studio command prompt, browse to the \<*drive*\>:\labs folder.  
  
3. At the command prompt, type **sn –k swift.snk**, and then press ENTER. Ensure that a success message appears in the output window.  
  
   > [!NOTE]
   >  If the correct message does not appear, use Visual Studio to troubleshoot your assembly.  
  
4. In Solution Explorer, right-click the **SWIFTSchemas** project, and then click **Properties**.  
  
5. In the SWIFTSchemas Property Pages dialog box, ensure that **Common Properties** is expanded, and then select **Assembly**.  
  
6. Scroll down the assembly properties in the right pane, and in the **Strong name** section, click the box to the right of **Assembly Key File**. Click the ellipsis button.  
  
7. In the Assembly Key File dialog box, browse to **\<*drive*:\>\labs**.  
  
8. Select the **swift.snk** file as the key file, and then click **Open**.  
  
9. In the SWIFTSchemas Property Pages dialog box, click **OK**.  
  
10. On the **File** menu, click **Save All** to save your changes.  
  
    Proceed to [Lesson 3: Adding SWIFT Schemas to a Project](../../adapters-and-accelerators/accelerator-swift/lesson-3-adding-swift-schemas-to-a-project.md).