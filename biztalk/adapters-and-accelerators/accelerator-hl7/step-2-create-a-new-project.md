---
title: "Step 2: Create a New Project | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "creating, projects"
  - "projects, creating"
  - "message enrichment tutorial, projects"
ms.assetid: 6e994845-53b8-4de8-a64f-32d36f7b5412
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 2: Create a New Project
In this step, you build a new solution by using the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)] environment. First, you create a new project (BTAHL7V22Common) that contains the three common schemas (for data types, segments, and table values) that the HL7 V2.2 schemas use, including the schema that you will use for the outgoing HL7 message. Second, you build another new project (BTAHL7V2XCommon) that contains the common standard schema used for headers in HL7 messages (MSH_25_GLO_DEF).  
  
### To create a new project  
  
1. Start **Visual Studio**.  
  
2. On the **File** menu, point to **New**, and then click **Project**.  
  
3. In the New Project dialog box, expand the **BizTalk Projects** folder, and then click the **BTAHL7Projects** folder.  
  
4. In the **Templates** pane, click **BTAHL7V22Common Project**.  
  
5. In the **Name** field, type **BTAHL7V22Common** as the project name.  
  
6. In the **Location** field, type *\<drive\>***:\Tutorial** as the path, and then click **OK** to open the new project.  
  
   > [!NOTE]
   >  BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) adds a new project to Solution Explorer with the three common schemas:  
  
   - datatypes_22.xsd  
  
   - segments_22.xsd  
  
   - tablevalues_22.xsd  
  
     [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] creates the project folder and files in the \<*drive*\>:\Tutorial\BTAHL7V22Common folder.  
  
7. On the **File** menu, point to **New**, and then click **Project**.  
  
8. In the New Project dialog box, expand the **BizTalk Projects** folder, and then click the **BTAHL7Projects** folder.  
  
9. In the **Templates** pane, click **BTAHL7V2XCommon Project**.  
  
10. In the **Name** field, type **BTAHL7V2XCommon** as the project name.  
  
11. In the **Location** field, type *\<drive\>***:\Tutorial** as the path.  
  
12. In the **Solution** field, select **Add to Solution**, and then click **OK**.  
  
    > [!NOTE]
    >  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] adds a new project to Solution Explorer with the following schemas:  
  
    - ACK_24_GLO_DEF.xsd  
  
    - ACK_25_GLO_DEF.xsd  
  
    - MSH_25_GLO_DEF.xsd  
  
      [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] creates the project folder and files in the **\<drive\>:\Tutorial\BTAHL7V22Common\BTAHL72XCommon** folder.  
  
    Proceed to [Step 3: Assign a Strong Name to the Assembly](../../adapters-and-accelerators/accelerator-hl7/step-3-assign-a-strong-name-to-the-assembly.md).  
  
## See Also  
 [Message Enrichment Tutorial](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)