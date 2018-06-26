---
title: "Step 7: Sign and Build the Projects | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "message enrichment tutorial, projects"
  - "projects, building"
  - "projects, signing"
ms.assetid: b66e4dc1-4ec6-4ec0-a69a-419b116b19c1
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 7: Sign and Build the Projects
In this step, you assign a strong name and build the project to generate an assembly that contains the resources (the schema) that you created in [Step 6: Validate the Schemas](../../adapters-and-accelerators/accelerator-hl7/step-6-validate-the-schemas.md). This also ensures that there are no compile errors in the work you have completed so far.  
  
### To sign the BTAHL7 Project  
  
1.  In Solution Explorer, right-click **BTAHL7 Project**, and then click **Properties**.  
  
2.  In the BTAHL7 Project Property Pages dialog box, click **Assembly**.  
  
3.  In the right pane, scroll down to the **Strong name** section, click the field to the right of **Assembly Key File**, and then click the ellipsis (…) button.  
  
4.  In the Assembly Key File dialog box, browse to **\<*drive*\>:\Tutorial\BTAHL7V22Common\key.snk** (as created in [Step 3: Assign a Strong Name to the Assembly](../../adapters-and-accelerators/accelerator-hl7/step-3-assign-a-strong-name-to-the-assembly.md)), and then click **Open**.  
  
5.  Click **OK** to save changes.  
  
### To build the BTAHL7 Project  
  
- In Solution Explorer, right-click **BTAHL7 Project**, and then click **Deploy**. [!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)] compiles the assembly into a DLL file and saves it in the \<*drive*\>:\Tutorial\BTAHL7V22Common\Bin\Development folder.  
  
  Proceed to [Step 8: Create a Map with BizTalk Mapper](../../adapters-and-accelerators/accelerator-hl7/step-8-create-a-map-with-biztalk-mapper.md).  
  
## See Also  
 [Message Enrichment Tutorial](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)