---
description: "Learn more about: Lesson 3: Adding SWIFT Schemas to a Project"
title: "Lesson 3: Adding SWIFT Schemas to a Project"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Lesson 3: Adding SWIFT Schemas to a Project
Now that you have a solution and a new project, you can add items to the project. The first item you add is a schema for an MT103 SWIFT Payment message. When you select the Schema template, BizTalk Editor starts.  
  
### To add a new schema to the project  
  
1. In Solution Explorer, right-click the **SWIFTSchemas** project, point to **Add**, and then click **Existing Item**.  
  
2. In the Add Existing Item-SWIFTSchemas dialog box, browse to **\<*drive*\>:\Program Files\Microsoft BizTalk Accelerator for SWIFT \<version\> MessagePack\SWIFT Messages\A4SWIFT-SRG\<version\>\Base Schemas**.  
  
3. Select the **SWIFT Base Types.xsd** and the **SWIFT Common Data Types.xsd** schemas, and then click **Add**.  
  
   > [!NOTE]
   >  The SWIFT Base Types.xsd and the SWIFT Common Data Types.xsd schemas appear in Solution Explorer under the SWIFTSchemas project.  
  
4. In Solution Explorer, right-click the **SWIFTSchemas** project, point to **Add**, and then click **Existing Item**.  
  
5. In the Add Existing Item-SWIFTSchemas dialog box, browse to the **\<*drive*\>:\Program Files\Microsoft BizTalk Accelerator for SWIFT \<version\> MessagePack\SWIFT Messages\A4SWIFT-SRG\<version\>\Category 1\MT103** folder.  
  
6. Select the **MT103.xsd** schema, and then click **Add**.  
  
   > [!NOTE]
   >  The new schema, MT103.xsd, appears in Solution Explorer under the SWIFTSchemas project.  
  
7. In Solution Explorer, double-click **MT103.xsd** to view the schema in BizTalk Editor.  
  
   > [!NOTE]
   >  The schema tree (left pane) and XSD view (right pane) appear in BizTalk Editor.  
  
8. On the **File** menu, click **Save All** to save your changes.  
  
   Proceed to [Lesson 4: Building and Deploying the Assembly](../../adapters-and-accelerators/accelerator-swift/lesson-4-building-and-deploying-the-assembly.md).
