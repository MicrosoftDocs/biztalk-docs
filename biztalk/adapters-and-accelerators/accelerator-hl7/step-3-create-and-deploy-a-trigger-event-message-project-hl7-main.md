---
title: "Step 3: Create and Deploy a Trigger Event (Message) Project_hl7_main | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "interrogative tutorial, trigger events"
ms.assetid: 90b65ad1-7953-4009-a1eb-1c2a85c7980a
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 3: Create and Deploy a Trigger Event (Message) Project_hl7_main
In this step, you create the schema used by a trigger event message. For example, the Admissions Discharge and Transfer system (ADT) that sends a message to the Hospital Information System (HIS). You use this schema to define the format of your message.  
  
### To create the project for the trigger event message  
  
1. In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.  
  
2. In the New Project dialog box, in the **Project Types** list, expand **BizTalk Projects**, and then click **BTAHL7Projects**.  
  
3. In the **Templates** list, click **Empty BTAHL7 Project**.  
  
4. In the **Name** field, type **BTAHL7V24Body Project**, and then click **OK**.  
  
5. In Solution Explorer, under the node for your new **BTAHL7V24Body** project, right-click **References**, and then click **Add Reference**.  
  
6. In the Add Reference dialog box, click the **Projects** tab, select **Interrogative_24Schemas**, click **Add**, and then click **OK**.  
  
## Step 3A: Add the Schemas  
 Use the following procedure to add the new schemas to the project.  
  
#### To add the schemas to the project  
  
1.  In Solution Explorer, right-click **BTAHL7V24Body Project**, point to **Add**, and then click **New Item**.  
  
2.  In the Add New Item dialog box, expand **BizTalk Project Items**, and then double-click **BTAHL7 Schemas** in the right pane.  
  
3.  In the HL7 Schema Selector dialog box, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Message Class**|Keep **V2.X** selected.|  
    |**Version**|Select **2.4**.|  
    |**Message Type**|Select **QRY**.|  
    |**Trigger Event**|Select **Q01**.|  
  
4.  Click **Finish** to add the schema to the project.  
  
     This creates the query schema file QRY_Q01_24_GLO_DEF.xsd.  
  
    > [!NOTE]
    >  Do not close the HL7 Schema Selector dialog box.  
  
5.  In the HL7 Schema Selector dialog box, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Message Class**|Keep **V2.X** selected.|  
    |**Version**|Select **2.4**.|  
    |**Message Type**|Select **DSR**.|  
    |**Trigger Event**|Select **Q01**.|  
  
6.  Click **Finish** to add the schema to the project.  
  
     This creates the response schema file DSR_Q01_24_GLO_DEF.xsd.  
  
7.  Click **Cancel** to close the **HL7 Schema Selector** dialog box.  
  
## Step 3B: Assign a Strong Key to the Assembly and Deploy  
 Use the following procedure to assign a strong key to the assembly and then deploy the assembly.  
  
#### To assign a strong key and deploy the assembly  
  
1. In Solution Explorer, right-click **BTAHL7V24Body** project, and then click **Properties**.  
  
2. In the **BTAHL7V24Body Property Pages** dialog box, click **Assembly**.  
  
3. In the right pane, scroll down to the **Strong name** section, click the field to the right of **Assembly Key File**, and then click the ellipsis (…) button.  
  
4. In the **Assembly Key File** dialog box, browse to \<*drive*\>:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator for HL7\SDK\Interrogative Tutorial, click **key.snk**, and then click **Open**.  
  
5. In the **BTAHL7V24Body Property Pages** dialog box, click **OK** to save your changes.  
  
6. In Solution Explorer right-click **BTAHL7V24Body Project**, and then click **Deploy**. Ensure a success message appears in the output window.  
  
   > [!NOTE]
   >  If a successful deploy message does not appear, use [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to troubleshoot your schemas.  
  
   Proceed to [Step 4: Create the Receive Port for Accepting ADT Query Messages](../../adapters-and-accelerators/accelerator-hl7/step-4-create-the-receive-port-for-accepting-adt-query-messages.md).