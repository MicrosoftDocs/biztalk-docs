---
title: "Step 2: Add Common Schemas for v2.3.1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: da98fe6c-4776-4cb8-8454-af3128dea4ab
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 2: Add Common Schemas for v2.3.1
In this step, you create a new project based on the BTAHL7231Common Project template. This template contains the three common schemas (for data types, segments, and table values) that [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) uses to validate v2.3.1 message instances. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] uses these common schemas in conjunction with the HL7 v2.3.1 schemas, including the schema that you will use for the individual messages in the incoming batch (ADT^A03).  
  
 At the end of the step, you assign a strong key to the assembly and deploy. You do not have to create a second strong key; you can use the strong key that you created in [Step 1: Add Header and Acknowledgment Schemas](../../adapters-and-accelerators/accelerator-hl7/step-1-add-header-and-acknowledgment-schemas.md).  
  
### To add v2.3.1 common schemas and deploy the assembly  
  
1. In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.  
  
2. In the New Project dialog box, in the **Project Types** section, expand **BizTalk Projects**, and then select **BTAHL7Projects**.  
  
3. In the **Templates** section, select **BTAHL7V231Common Project**.  
  
4. In the **Name** box, enter **BTAHL7V231Common Project** as the project name.  
  
5. In the **Solution** box, select **Add to Solution**.  
  
6. Click **OK**.  
  
   > [!NOTE]
   >  In Solution Explorer, three schemas (datatypes_231.xsd, segments_231.xsd, and tablevalues_231.xsd) are included in the project.  
  
7. In Solution Explorer, right-click **BTAHL7V231Common Project**, and then click **Properties**.  
  
8. On the BTAHL7V231Common Property Pages dialog box, click **Signing**.  
  
9. Check **Sign the assembly** check box.  
  
10. In Choose a strong name key file drop down list select.  
  
11. Browse to **:\Batching Tutorial**, select **key.snk**, and then click **Open**.  
  
12. Right-click **BTAHL7V231Common**, and then click **Deploy**. Ensure a success message appears in the output window.  
  
    > [!NOTE]
    >  If the correct message does not appear, use [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to troubleshoot your schemas.  
  
    Proceed to [Step 3: Add a Trigger Event (Message) Schema](../../adapters-and-accelerators/accelerator-hl7/step-3-add-a-trigger-event-message-schema.md).