---
title: "Step 3: Add a Trigger Event (Message) Schema | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fc4a67d9-9582-4f2b-9bc9-18fbff823d29
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 3: Add a Trigger Event (Message) Schema
In this step, you create a new project based on the Empty [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Project template. To this project, you add the schema that [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] will use to validate the messages in the incoming batch (ADT^A03). You add a reference to the project containing the v2.3.1 common schemas, assign the strong name to the project, and then deploy the project.  

### To add the project containing the message schema  

1. In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.  

2. In the New Project dialog box, in the **Project Types** section, expand **BizTalk Projects**, and then select **BTAHL7Projects**.  

3. In the **Templates** section, select **Empty BTAHL7 Project**.  

4. In the **Name** box, enter **BTAHL7V231Body** as the project name.  

5. In the **Solution** box, select **Add to Solution**.  

6. Click **OK**.  

7. In Solution Explorer, under the node for your new project, right-click **References**, and then click **Add Reference**.  

8. In the Add Reference dialog box, on the **Projects** tab, click **BTAHL7V231Common Project** in the **Project Name** column, click **Add**, and then click **OK**.  

### To add the schema to the project  

1. In Solution Explorer, right-click **BTAHL7V231Body**, point to **Add**, and then click **New Item**.  

2. In the Add New Item dialog box, expand **BizTalk Project Items**, and then click **BTAHL7 Schemas**. In the **Templates** pane, click **BTAHL7 Schemas**, and then click **Add**.  

3. In the **HL7 Schema Selector** dialog box, do the following:  


   |     Use this      |         To do this         |
   |-------------------|----------------------------|
   | **Message Class** | Keep **V2.X** as selected. |
   |    **Version**    |     Select **2.3.1**.      |
   | **Message Type**  |      Select **ADT**.       |
   | **Trigger Event** |      Select **A03**.       |


4. Click **Create** to add the schema to the project, then click **Cancel** to close the dialog box. Note that BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) has added the ADT_A03_231_GLO_DEF.xsd schema to the BTAHL7V231Body project.  

### To assign a strong key and deploy  

1. In Solution Explorer, right-click **BTAHL7V231Body**, and then click **Properties**.  

2. In the BTAHL7V231Body Property Page dialog box, click **Signing**.  

3. Check **Sign the assembly** check box.  

4. In **Choose a strong name key file** drop down list select **\<Browse…\>.**  

5. Browse to **\<*drive*\>:\Batching Tutorial**, select **key.snk**, and then click **Open**.  

6. In Solution Explorer, right-click **BTAHL7V231Body**, and then click **Deploy**. Ensure that a success message appears in the output window.  

   > [!NOTE]
   >  If a successful-deploy message does not appear, use [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to troubleshoot your schemas.  

   Proceed to [Step 4: Create a Receive Port for Accepting the Batch Message](../../adapters-and-accelerators/accelerator-hl7/step-4-create-a-receive-port-for-accepting-the-batch-message.md).