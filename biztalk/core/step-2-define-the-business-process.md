---
title: "Step 2: Define the Business Process | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b37bd9f1-5ee2-434d-950a-cf12967b6fc2
caps.latest.revision: 49
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 2: Define the Business Process
![Step 2 of 4](../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")  
  
 **Time to complete:** 8 minutes  
  
 **Objective:** In this step, you use Orchestration Designer to define your business process.  
  
 **Purpose:** The workflow of the orchestration represents and automates your company's business process for approving inventory replenishment requests.  
  
## Prerequisites  
 Note the following requirements before you begin this step:  
  
-   Before you begin this step you must complete [Step 1: Add EAIOrchestration Project to the Solution](../core/step-1-add-eaiorchestration-project-to-the-solution.md).  
  
## Procedures  
 The first step for developing an orchestration is to use action shapes to represent the business process.  
  
#### To create the EAI business process workflow  
  
1. From Visual Studio, in Solution Explorer, double-click **EAIProcess.odx** to open the orchestration.  
  
2. In Orchestration Designer, from the orchestration Toolbox, drag the **Receive** shape, and drop it between the **Begin** (green circle) and **End** (red octagon) shapes.  
  
   > [!NOTE]
   >  If the Toolbox is not open, in the **View** menu, click **Toolbox**. To anchor it on the screen, click the thumbtack icon.  
  
3. From the toolbox, drag the **Decide** shape beneath the Receive shape.  
  
4. From the toolbox, drag the **Transform** shape to the left branch of the Decide shape. The Transform shape is nested inside the Construct Message shape.  
  
5. From the toolbox, drag the **Send** shape beneath the Transform shape.  
  
6. From the toolbox, drag the **Send** shape to the right branch of the Decide shape.  The orchestration looks like the following after you added the action shapes:  
  
    ![EAI process](../core/media/eaiprocess.gif "EAIProcess")  
  
   The next step is to define message variables.  Several action shapes have a message property that needs to be specified.  
  
#### To define message variables  
  
1.  From Visual Studio, click the **View** menu, click **Other Windows**, and then click **Orchestration View**.  
  
2.  From Orchestration View, right-click **Messages**, and then click **New Message**.  
  
3.  In the Properties window, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Identifier**|Type **RequestMessage**.|  
    |**Message Type**|Click **Schemas**, and then click **\<Select from referenced assembly …\>**. From the Select Artifact Type window, click **EAISchemas**, and then click **Request**. Click **OK**|  
  
4.  From Orchestration View, right-click **Messages**, and then click **New Message**.  
  
5.  In the Properties window, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Identifier**|Type **RequestDeclineMessage**.|  
    |**Message Type**|Click **Schemas**, and then click **\<Select from referenced assembly …\>**. From the Select Artifact Type window, click **EAISchemas**, and then click **RequestDecline**. Click **OK**|  
  
#### To configure the properties of the shapes  
  
1.  On the design surface, click the **Receive** shape to select it.  
  
2.  In the Properties window, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Name**|Type **ReceiveRequest**.|  
    |**Message**|Select **RequestMessage**.|  
    |**Activate**|From the drop-down list, select **True**.|  
  
    > [!NOTE]
    >  If the Property window is not open, in the **View** menu, click **Properties Window**.  
  
3.  On the design surface, click the **Decide** shape.  
  
4.  In the Properties window, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Name**|Type **CheckGrandTotal**.|  
  
    > [!NOTE]
    >  If the Property window is not open, in the **View** menu, click **Properties Window**.  
  
5.  On the design surface, click the **Rule_1** shape.  
  
6.  In the Properties window, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Name**|Type **DeclineRule**.|  
    |**Expression**|Click the ellipses (**…**), and then type `RequestMessage(EAISchemas.PropertySchema.GrandTotal ) > 10000`. Click **OK**.|  
  
7.  On the design surface, click the **ConstructMessage_1** shape.  
  
8.  In the Properties window, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Name**|Type **ConstructRequestDeclineMessage**.|  
    |**Messages Constructed**|Select **RequestDeclineMessage**.|  
  
9. On the design surface, click the **Transform_1** shape.  
  
10. In the Properties window, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Name**|Type **TransformRequestToRequestDeclineMessage**.|  
    |**Map Name**|Click **…**. From Transform Configuration, do the following:<br /><br /> Enter the configuration information:<br /><br /> - Click **Existing Map**.<br /><br /> Fully Qualified Map Name:<br /><br /> - Select **\<Select from referenced assembly\>**.  From the left pane, select **EAISchemas**.  From the right pane, select EAISchemas.MapToReqDecline.  Click **OK**.<br /><br /> Source<br /><br /> - RequestMessage<br /><br /> Destination<br /><br /> - RequestDeclineMessage|  
  
11. On the design surface, click the **Send_1** shape.  
  
12. In the Properties window, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Name**|Type **SendRequestDecline**.|  
    |**Message**|Select **RequestDeclineMessage**.|  
  
13. On the design surface, click the **Send_2** shape.  
  
14. In the Properties window, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Name**|Type **SendRequestToERP**.|  
    |**Message**|Select **RequestMessage**.|  
  
## What did I just do?  
 In this step, you used Orchestration Designer to define your business process.  
  
## Next Steps  
 You add logical ports to the orchestration in [Step 3: Add Ports to the Orchestration](../core/step-3-add-ports-to-the-orchestration.md).  
  
## See Also  
 [Step 1: Add EAIOrchestration Project to the Solution](../core/step-1-add-eaiorchestration-project-to-the-solution.md)   
 [Step 3: Add Ports to the Orchestration](../core/step-3-add-ports-to-the-orchestration.md)   
 [Step 4: Build the EAIOrchestration Project](../core/step-4-build-the-eaiorchestration-project.md)