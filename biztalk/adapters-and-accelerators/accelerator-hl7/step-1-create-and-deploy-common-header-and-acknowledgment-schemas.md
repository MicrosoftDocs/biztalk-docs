---
title: "Step 1: Create and Deploy Common Header and Acknowledgment Schemas | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "interrogative tutorial, headers"
ms.assetid: e0f11f58-9a8c-4567-a537-3d182fa7dce2
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 1: Create and Deploy Common Header and Acknowledgment Schemas
You use the header schema to validate the header (MSH segment) of the message instance. You use the acknowledgment schema to generate the acknowledgment for the message instance. This process is common across all HL7 schema versions.  
  
### To create the header and acknowledgment schemas  
  
1. Start **Microsoft Visual Studio 2012**.  
  
2. In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.  
  
3. In the New Project dialog box, in the **Project Types** list, expand **BizTalk Projects**, and then select **BTAHL7Projects**.  
  
4. In the **Templates** list, select **BTAHL7V2XCommon Project**.  
  
5. In the **Name** field, type **Interrogative_2XSchemas**, and then click **OK**.  
  
    In Solution Explorer, notice that three schemas (ACK_24_GLO_DEF.xsd, ACK_25_GLO_DEF.xsd, and MSH_25_GLO_DEF.xsd) are included in the project.  
  
    Leave Visual Studio open.  
  
## Step 1A: Assign a Strong Key to the Assembly and Deploy  
 Use the following procedure to assign a strong key to the assembly and then deploy the assembly.  
  
#### To assign a strong key and deploy the assembly  
  
1. Start **Visual Studio 2012 Command Prompt**.  
  
2. At the [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] command prompt, change your directory to the \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\Interrogative Tutorial folder.  
  
3. At the command prompt, type **sn –k key.snk**, and then press **Enter**. Ensure that a success message appears in the output window.  
  
   > [!NOTE]
   >  If the correct message does not appear, use [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to troubleshoot your assembly.  
  
4. In Solution Explorer, right-click **Interrogative_2XSchemas** project, and then click **Properties**.  
  
5. In the Interrogative_2XSchemas Property Pages dialog box, click **Assembly**.  
  
6. In the right pane, scroll down to the **Strong name** section, click the field to the right of **Assembly Key File**, and then click the ellipsis (…) button.  
  
7. In the Assembly Key File dialog box, browse to \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\Interrogative Tutorial, click **key.snk**, and then click **Open**.  
  
8. In the Interrogative_2XSchemas Property Pages dialog box, click **OK** to save your changes.  
  
9. In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], in Solution Explorer, right-click **Interrogative_2XSchemas** project, and then click **Deploy**. Ensure a success message appears in the output window.  
  
   > [!NOTE]
   >  If the correct deploy message does not appear, use [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to troubleshoot your deployment.  
  
   Proceed to [Step 2: Create Common Schemas for V2.4](../../adapters-and-accelerators/accelerator-hl7/step-2-create-common-schemas-for-v2-4.md).