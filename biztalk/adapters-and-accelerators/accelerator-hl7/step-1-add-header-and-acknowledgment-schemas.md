---
title: "Step 1: Add Header and Acknowledgment Schemas | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 808132bf-02e7-4ff4-b914-9fae5d27e5fd
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 1: Add Header and Acknowledgment Schemas
In this step, you create a new project based on the BTAHL72XCommon Project template. This template contains the three common schemas for message headers (MSH_25_GLO_DEF.xsd) and acknowledgments (ACK_24_GLO_DEF.xsd) and (ACK_25_GLO_DEF.xsd). You must include these schemas in a project so that BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) builds and/or validates the message headers and acknowledgments correctly. This process is common across all schema versions of [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 2.X.  
  
 You also create a strong key, assign it to the assembly, and then deploy the assembly. The strong key provides security and identity to the assembly, and is necessary for deployment. When you deploy the assembly, it is stored in the Configuration database (also known as the BizTalk Management database) and the global assembly cache (GAC).  
  
### To create the project and add header and acknowledgment schemas  
  
1. In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.  
  
2. In the New Project dialog box, in the **Project Types** list, expand **BizTalk Projects**, and then click **BTAHL7Projects**.  
  
3. In the **Templates** list, click **BTAHL7V2XCommon Project**.  
  
4. In the **Name** box, type **BTAHL7V2XCommon** as the project name.  
  
5. In the **Location** box, browse to **\<**<em>drive</em>**:\>\Batching Tutorial**.  
  
6. Click **OK**.  
  
> [!NOTE]
>  In Solution Explorer, three schemas (MSH_25_GLO_DEF.xsd, ACK_24_GLO_DEF.xsd, and ACK_25_GLO_DEF.xsd) are included in the project.  
  
### To assign a strong key to the assembly and deploy  
  
1. Open **Visual Studio Command Prompt**.  
  
2. On the [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] command prompt, browse to the **\<**<em>drive</em>**\>:\Batching Tutorial** folder.  
  
3. At the command prompt, type **sn –k key.snk**, and then press ENTER. Ensure that a success message appears in the output window.  
  
   > [!NOTE]
   >  If the correct message does not appear, use [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to troubleshoot your assembly.  
  
4. In Solution Explorer, right-click **BTAHL7V2Xcommon Project**, and then click **Properties**.  
  
5. In the **BTAHL7V2XCommon Project Property Page** dialog box, click **Signing**.  
  
6. Check **Sign the assembly** check box.  
  
7. In **Choose a Strong name** key file drop down list select **\<Browse…\>**.  
  
8. Browse to \<*drive*\>:\Batching Tutorial, select **key.snk**, and then click **Open**.  
  
9. In the BTAHL7V2XCommon Project Property Pages window, click **OK** to save your changes.  
  
10. In Solution Explorer, right-click **BTAHL7V2Xcommon Project**, and then click **Deploy**. Ensure a success message appears in the output window.  
  
    > [!NOTE]
    >  If the correct deploy message does not appear, use [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to troubleshoot your deployment.  
  
    Proceed to [Step 2: Add Common Schemas for v2.3.1](../../adapters-and-accelerators/accelerator-hl7/step-2-add-common-schemas-for-v2-3-1.md).