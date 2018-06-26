---
title: "Step 10: Create an Orchestration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "orchestrations, creating"
  - "creating, orchestrations"
  - "message enrichment tutorial, orchestrations"
ms.assetid: 10f5cf3d-4a34-4c80-89d1-c390552cfc09
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 10: Create an Orchestration
In this step, you use Orchestration Designer to create an orchestration to represent the business process for retrieving additional patient details to fully populate an ADT_A04 message. Using Orchestration Designer, you select the orchestration shapes required to represent actions for this business process. In later exercises, you provide additional information to configure the shapes so that they can function properly.  
  
> [!NOTE]
>  The orchestration created in the following steps only works in the context of this tutorial. In order for the orchestration to work correctly, it needs the assembly references, maps, and the other artifacts that you create while using this tutorial.  
  
### To create an orchestration  
  
1. In Solution Explorer, right-click **BTAHL7 Project**, point to **Add**, and then click **New Item**.  
  
2. In the **Add New Item** dialog box, in the **Categories** pane, click **Orchestration Files**.  
  
3. In the **Templates** pane, click **BizTalk Orchestration**.  
  
4. In the **Name** field, type **Doorbell Orchestration.odx** (note that there is a space between the word **Doorbell** and **Orchestration**) as the orchestration name, and then click **Add** to create a new orchestration file.  
  
5. In the **View** menu, click **Toolbox**.  
  
6. In the **Toolbox** pane, drag the **Receive** shape to the Design view surface and drop it on the area labeled **Drop a shape from the toolbox here**.  
  
7. In the Properties window (on the bottom right of your screen), click the **Name** property and type **DoorbellReceive** as the name of the **Receive** shape, and then press **Enter**.  
  
8. In the Properties window, change the **Activate** property to **True**.  
  
9. Drag the **Transform** shape from the Toolbox and drop it directly below the **DoorbellReceive** shape.  
  
10. In the Properties window (on the bottom right of your screen), click the **Name** property to change the name of the **Transform** shape to **DoorbellTransform**, and then press **Enter**.  
  
11. In the **Toolbox** pane, drag the **Message Assignment** shape to the Design view surface and drop it on the area directly below the **ConstructMessage_1** shape.  
  
12. In the orchestration Design view surface, click the **MessageAssignment_1** shape, and in the **Properties** pane, click **Name** and type the new name **DoorbellFinalTransform**, and then press **Enter**.  
  
13. Drag the **Send** shape from the Toolbox and drop it on the connecting line directly below the **DoorbellFinalTransform** shape.  
  
14. In the Properties window (on the bottom right of your screen), click the **Name** property to change the name of the **Send** shape to **DoorbellSend**, and then press **Enter**.  
  
    Proceed to [Step 11: Create Orchestration Variables](../../adapters-and-accelerators/accelerator-hl7/step-11-create-orchestration-variables.md).  
  
## See Also  
 [Message Enrichment Tutorial](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)