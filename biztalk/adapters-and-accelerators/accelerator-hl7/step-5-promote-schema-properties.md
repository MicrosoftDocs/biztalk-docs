---
title: "Step 5: Promote Schema Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "message enrichment tutorial, pomoted properties"
  - "promoted properties"
  - "schemas, promoted properties"
ms.assetid: cb51cece-1b65-4ba2-b8e6-ce8b6694cdb6
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 5: Promote Schema Properties
In this step, you promote schema properties so that a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] orchestration can reference those property values that you create in later steps. Promotion is a mechanism that you use to reference a specific value within a message instance and make it accessible to [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] components such as orchestration or for content-based routing purposes. Additionally, a promoted property is visible by [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] IntelliSense in the Expression Editor of [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].  
  
> [!NOTE]
>  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] auditing and logging functionality with the BizTalk Health and Activity Tracking (HAT) tool can track only promoted schema properties.  
  
### To promote schema properties  
  
1. In Solution Explorer, under **BTAHL7 Project**, double-click the **DoorBell.xsd** node to open the schema.  
  
2. Right-click the **FirstName** field element, point to **Promote**, and then click **Quick Promotion**.  
  
3. Click **OK** to add the property schema to the project.  
  
   > [!NOTE]
   >  [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] adds an orange circle to the icon for the **FirstName** element, indicating that the element has been promoted.  
  
4. Repeat these steps to promote the following field elements:  
  
   -   **MiddleName**  
  
   -   **LastName**  
  
   -   **SSN**  
  
   > [!IMPORTANT]
   >  It is important to note that promoting a patient ID (PID) such as a social security number (SSN) causes [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] to track that property for every inbound message through the system. The side effect of this situation is that the message-tracking database keeps a copy of patient SSNs. This can create a significant security issue. You must either protect this data store with extreme care or avoid the promotion of PID data completely.  
  
    For more information about tracking documents based on the schema elements that you promoted, see BizTalk Server Help for information on Health and Activity Tracking.  
  
   Proceed to [Step 6: Validate the Schemas](../../adapters-and-accelerators/accelerator-hl7/step-6-validate-the-schemas.md).  
  
## See Also  
 [Message Enrichment Tutorial](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)