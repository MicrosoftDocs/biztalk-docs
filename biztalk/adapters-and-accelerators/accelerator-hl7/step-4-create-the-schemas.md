---
title: "Step 4: Create the Schemas | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "message enrichment tutorial, schemas"
  - "creating, schemas"
  - "schemas, creating"
ms.assetid: 81b1f538-9743-433a-87f9-a423dcb868c8
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 4: Create the Schemas
In this step, you create a new project (**BTAHL7 Project**) that contains the artifacts for this project: the schemas, map, and orchestration. You then create a schema (**Doorbell.xsd**) for the incoming XML-encoded message, and select an existing schema (**ADT_A04_22_GLO_DEF.xsd**) for the outgoing HL7-encoded message. You use these schemas to define the structure of the messages that you exchange within the orchestration.  

### To create the schemas  

1. On the **File** menu, point to **New**, and then click **Project**.  

2. In the New Project dialog box, expand the **BizTalk Projects** folder, and then click the **BTAHL7Projects** folder.  

3. In the **Templates** pane, click **Empty BTAHL7 Project**.  

4. In the **Name** field, type **BTAHL7 Project** as the project name.  

5. In the **Solution** field, select **Add to Solution**.  

6. In the **Location** field, verify that **\<*drive*\>:\Tutorial\BTAHL7V22Common** is the path.  

7. Click **OK** to open the new project.  

   > [!NOTE]
   >  [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] adds a new project to Solution Explorer. It also adds the project folder and creates files in the \<*drive*\>:\Tutorial\\**BTAHL7V22Common** Project folder.  

8. In Solution Explorer, right-click the **BTAHL7 Project** project, point to **Add**, and then click **New Item**.  

9. In the Add New Item - BTAHL7 Project dialog box, in the **Categories** pane, click **Schema Files**, and in the **Templates** pane, click **Schema**.  

10. In the **Name** field, type **Doorbell.xsd** to name the schema.  

11. Click **Add** to open the blank schema in BizTalk Editor.  

12. In the **\<Schema\>** tree, right-click the **Root** node, and then click **Rename**.  

13. Type **DoorbellRoot** as the new name, and then press **Enter**.  

14. Right-click the **DoorbellRoot** node, point to **Insert Schema Node**, and then click **Child Field Element** to add the following fields (repeat this step for each field element):  

    -   **FirstName**  

    -   **MiddleName**  

    -   **LastName**  

    -   **SSN**  

15. In Solution Explorer, right-click **BTAHL7 Project**, point to **Add**, and then click **New Item**.  

16. In the Add New Item - BTAHL7 Project dialog box, in the **Categories** pane, click **BTAHL7 Schemas**, and then click **Add**.  

17. In the HL7 Schema Selector dialog box, in the **Message Class** box, select **V2.X**, and in the **Schema Details** pane, do the following:  


    |     Use this      |                                     To do this                                     |
    |-------------------|------------------------------------------------------------------------------------|
    |    **Version**    |    Select the version number of the HL7 message. In this tutorial, use **2.2**.    |
    | **Message Type**  |           Select the type of HL7 message. In this tutorial, use **ADT**.           |
    | **Trigger Event** | Select the Trigger Event value for the HL7 message. In this tutorial, use **A04**. |


18. Click **Finish** to add the ADT_A04_22_GLO_DEF.xsd (Register Patient) schema to your project. Close the HL7 Schema Selector dialog box.  

19. In Solution Explorer, under **BTAHL7 Project**, right-click **References** and then click **Add Reference**.  

20. In the Add Reference dialog box, on the **Projects** tab, select the **BTAHL7V22Common** project, click **Add**, and then click **OK**.  

    > [!NOTE]
    >  This adds a reference to the original project so that [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] recognizes the HL7 schemas correctly.  

21. In Solution Explorer, under **BTAHL7 Project**, right-click **References** and then click **Add Reference**.  

22. In the Add Reference dialog box, click the **Browse** tab. In the **Look In** box, move to \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_BTAHL7Drop\Bin. Click **Microsoft.Solutions.BTAHL7.HL7Schemas.dll**, click **Add**, and then click **OK**.  

    Proceed to [Step 5: Promote Schema Properties](../../adapters-and-accelerators/accelerator-hl7/step-5-promote-schema-properties.md).  

## See Also  
 [Message Enrichment Tutorial](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)