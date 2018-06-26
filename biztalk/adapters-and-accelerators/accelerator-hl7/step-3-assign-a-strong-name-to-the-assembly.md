---
title: "Step 3: Assign a Strong Name to the Assembly | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "assemblies"
  - "message enrichment tutorial, strong name assemblies"
  - "strong name assemblies"
ms.assetid: 8709e4e1-b428-42af-ba3c-08225c17a9eb
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 3: Assign a Strong Name to the Assembly
In this step, you create and assign a strong name for the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] assembly. A strong-named assembly provides several security benefits and is required in order to deploy your project in the global assembly cache (GAC). A strong name guarantees the uniqueness of the assembly by assigning a digital signature and a unique key pair. This also protects the lineage of the assembly by ensuring that no one can generate a subsequent version of the assembly. Lastly, a strong name provides a strong integrity check to guarantee that the contents of the assembly have not changed since you built it.  
  
### To assign a strong name to the assembly  
  
1. Start **Visual Studio Command Prompt**.  
  
   > [!NOTE]
   >  If you have already created a strong name key, you can reuse it.  
  
2. At the command prompt, move to<strong>\<*drive*\>:\Tutorial\BTAHL7V22Common</strong> (where \<*drive*\> is your installation drive letter) and then press **Enter**.  
  
3. At the command prompt, type **sn –k key.snk**, and then press **Enter**. A message appears indicating that [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] wrote the key pair to the key file key.snk.  
  
4. In Solution Explorer, right-click the **BTAHL7V22Common** project, and then click **Properties**.  
  
5. In the BTAHL7V22Common Property Pages dialog box, click **Assembly**.  
  
6. In the right pane, scroll down to the **Strong name** section, click the field to the right of **Assembly Key File**, and then click the ellipsis (…) button.  
  
7. In the Assembly Key File dialog box, browse to **\<*drive*\>:\Tutorial\BTAHL7V22Common\key.snk**, click **Open**, and then click **OK**.  
  
8. In Solution Explorer, right-click **BTAHL7V22Common**, and then click **Deploy**. [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] creates an assembly that you can reference from your next project.  
  
9. Repeat steps 4 through 8 for the BTAHL7V2XCommon project.  
  
   Proceed to [Step 4: Create the Schemas](../../adapters-and-accelerators/accelerator-hl7/step-4-create-the-schemas.md).  
  
## See Also  
 [Message Enrichment Tutorial](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)