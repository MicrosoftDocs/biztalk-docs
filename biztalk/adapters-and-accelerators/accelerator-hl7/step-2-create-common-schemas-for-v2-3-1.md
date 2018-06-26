---
title: "Step 2: Create Common Schemas for V2.3.1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "end-to-end tutorial, common schemas"
  - "common schemas"
ms.assetid: db1a2206-559f-475a-803d-55522cce007e
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 2: Create Common Schemas for V2.3.1
The V2.3.1 schemas are commonly referenced schemas, which you use to validate the message instance.  
  
### To create a common schema for V2.3.1  
  
1. In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.  
  
2. In the New Project dialog box, in the **Project Types** section, expand **BizTalk Projects**, and then select **BTAHL7Projects**.  
  
3. In the Templates section, select **BTAHL7V231Common Project**.  
  
4. In the **Name** box, enter **BTAHL7V231Common Project** as the project name.  
  
5. In the **Solution** box, select **Add to Solution**.  
  
6. Click **OK**.  
  
   > [!NOTE]
   >  In Solution Explorer, three schemas (datatypes_231.xsd, segments_231.xsd, and tablevalues_231.xsd) are included in the project.  
  
7. In Solution Explorer, right-click **BTAHL7V231Common Project**, and then click **Properties**.  
  
8. On the BTAHL7V231Common Property Page, click **Signing**.  
  
9. Select the **Sign the assembly** check box.  
  
10. In **Choose a strong name key file**, select **\<Browse…\>** .  
  
11. Browse to \<drive\>:\Batching Tutorial, select **key.snk**, and then click **Open**.  
  
12. In Solution Explorer, right-click **BTAHL7V231Common Project**, and then click **Deploy**. Ensure a success message appears in the output window.  
  
    > [!NOTE]
    >  If the correct message does not appear, use [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to troubleshoot your schemas.  
  
    Proceed to [Step 3: Add a Trigger Event (Message) Schema](../../adapters-and-accelerators/accelerator-hl7/step-3-add-a-trigger-event-message-schema.md).