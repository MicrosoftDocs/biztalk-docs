---
title: "Step 3: Create and Deploy a Trigger Event (Message) Project | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "end-to-end tutorial, trigger events"
  - "trigger events"
ms.assetid: 5d21a923-fc2c-4d50-b146-daca0aa26e2a
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 3: Create and Deploy a Trigger Event (Message) Project
In this step, you create the schema for your trigger event message. For example, you might be the Admissions Discharge and Transfer system (ADT) who sends a message to the Hospital Information System (HIS). You need this schema to define the format of your message.  
  
### To create the project for the trigger event message  
  
1. In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, then click **Project**.  
  
2. In the New Project dialog box, in the **Project Types** section, expand **BizTalk Projects**, and then click **BTAHL7Projects**.  
  
3. In the Templates section, click **Empty BTAHL7 Project**, in the **Name** box, type **BTAHL7V231Body Project**, and then click **OK**.  
  
4. In Solution Explorer, under the node for your new project, right-click **References**, and then click **Add Reference**.  
  
5. In the Add Reference dialog box, on the **Projects** tab, select **BTAHL7V231Common Project1**, click **Add**, and then click **OK**.  
  
## Step 3A: Add the Schema  
 Use the following procedure to add the new schema to the project.  
  
#### To add the schema to the project  
  
1.  In Solution Explorer, right-click **BTAHL7V231Body Project**, point to **Add**, and then click **New Item**.  
  
2.  In the Add New Item dialog box, in the **Categories** section, expand **BizTalk Project Items**, and then select **BTAHL7 Schemas**.  
  
3.  In the Templates section, double-click **BTAHL7 Schemas**.  
  
4.  In the HL7 Schema Selector dialog box, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Message Class**|Leave the default of **V2.X** selected.|  
    |**Version**|Select **2.3.1**.|  
    |**Message Type**|Select **ADT**.|  
    |**Trigger Event**|Select **A03**.|  
  
5.  Click **Finish** to add the schema to the project.  
  
## Step 3B: Assign a Strong Key to the Assembly and Deploy  
 Use the following procedure to assign a strong key to the assembly and then deploy the assembly.  
  
#### To assign a strong key and deploy the assembly  
  
1. In Solution Explorer, right-click **BTAHL7V231Body Project**, and then click **Properties**.  
  
2. In the Project Property Pages page, click **Assembly**.  
  
3. In the right pane, scroll down to the **Strong name** section, click the field to the right of **Assembly Key File**, and then click the ellipsis (**…**) button.  
  
4. In the Assembly Key File dialog box, browse to \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial, click **key.snk**, and then click **Open**.  
  
5. In the Project Property Pages dialog box, click **OK** to save your changes.  
  
6. In Solution Explorer right-click **BTAHL7V231Body Project**, and then click **Deploy**. Ensure a success message appears in the output window.  
  
   > [!NOTE]
   >  If a successful deploy message does not appear, use [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to troubleshoot your schemas.  
  
   Proceed to [Step 4: Create the Receive Port for Accepting ADT^A03 Messages from ADT Systems Using the MLLP Adapter](../../adapters-and-accelerators/accelerator-hl7/step-4-create-receive-port-to-accept-adt^a03-messages-from-adt-using-mllp.md).