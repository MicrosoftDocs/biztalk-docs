---
title: "Step 2: Create Common Schemas for V2.4 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "interrogative tutorial, common schemas"
ms.assetid: 333ae85a-a307-4ab1-97f4-4d7b986e91de
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 2: Create Common Schemas for V2.4
The V2.4 schemas are commonly referenced schemas, which you use to validate the query and response message instances.  
  
### To create the common schemas for V2.4  
  
1. In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.  
  
2. In the New Project dialog box, in the **Project Types** list, expand **BizTalk Projects**, and then select **BTAHL7Projects**.  
  
3. In the **Templates** list, select **BTAHL7V24Common Project**.  
  
4. In the **Name** field, type **Interrogative_24Schemas**.  
  
5. In the Solution field, select **Add to Solution**, and then click **OK**.  
  
    In Solution Explorer, notice that three schemas (datatypes_24.xsd, segments_24.xsd, and tablevalues_24.xsd) are included in the project.  
  
6. In Solution Explorer, right-click **Interrogative_24Schemas** project,and then click **Properties**.  
  
7. In the Interrogative_24Schemas Property Pages dialog box, click **Assembly**.  
  
8. In the right pane, scroll down to the **Strong name** section, click the field to the right of **Assembly Key File**, and then click the ellipsis (…) button.  
  
9. In the **Assembly Key File** dialog box, browse to \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\Interrogative Tutorial, click **key.snk**, and then click **Open**.  
  
10. In the Interrogative_24Schemas Property Pages dialog box, click **OK** to save your changes.  
  
11. In Solution Explorer, right-click **Interrogative_24Schemas** project, and then click **Deploy**. Click **OK** to the dialog box asking you to save changes to the solution. Ensure a success message appears in the output window.  
  
    > [!NOTE]
    >  If the correct message does not appear, use [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to troubleshoot your schemas.  
  
    Proceed to [Step 3: Create and Deploy a Trigger Event (Message) Project](../../adapters-and-accelerators/accelerator-hl7/step-3-create-and-deploy-a-trigger-event-message-project-hl7-main.md).