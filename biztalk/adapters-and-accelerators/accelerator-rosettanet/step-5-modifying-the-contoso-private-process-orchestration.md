---
title: "Step 5: Modifying the Contoso Private Process Orchestration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "private processes, orchestrations"
  - "private process tutorial, modifying private process orchestration"
ms.assetid: a5430db8-e5f0-48a6-abb9-e268d8ec2ec4
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 5: Modifying the Contoso Private Process Orchestration
In this step, you modify the private process orchestration to integrate with the Enterprise Resource Planning (ERP) system for Contoso. The ERP system for Contoso uses internally defined schemas for product price and availability. By customizing the private process for the 3A2 - Price and Availability Partner Interface Process (PIP), you will be able to integrate with the ERP system by using schema-mapping information.  
  
### To add a reference to the Contoso PriceAndAvailability and RNPIPs assemblies  
  
1. With the Contoso solution displayed in Solution Explorer, right-click the **PrivateResponder** project, and then click **Add Reference**.  
  
2. In the Add Reference dialog box, click **Browse**. Move to *\<drive\>*:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\Bin folder, and then select the following assemblies<strong>:</strong>  
  
   -   Microsoft.Solutions.BTARN.CommonTypes.dll  
  
   -   Microsoft.Solutions.BTARN.ConfigurationManager.dll  
  
   -   Microsoft.Solutions.BTARN.GlobalSchemas.dll  
  
   -   Microsoft.Solutions.BTARN.PublicResponder.dll  
  
   -   Microsoft.Solutions.BTARN.Schemas.RNPIPs.dll  
  
   -   Microsoft.Solutions.BTARN.Shared.dll  
  
   -   Microsoft.Solutions.BTARN.XSDClasses.GlobalSchemas.dll  
  
3. Click **Add**.  
  
4. In the Add Reference dialog box, click the **Projects** tab, select the **ContosoPriceAndAvailability** and **HeaderHelper** projects, and then click **Add**.  
  
5. Click **OK**.  
  
6. In the Microsoft Development Environment dialog box, click **OK**.  
  
### To create new message types  
  
1.  In Solution Explorer, double-click the **PrivateResponder** orchestration to open it.  
  
2.  In Solution Explorer, click **Orchestration View**.  
  
3.  In Orchestration View, right-click **Messages**, and then click **New Message**.  
  
4.  In the Properties window, in the **Identifier** box, type **PIP3A2RequestMessage**.  
  
5.  In the **Message Type** box, click the drop-down arrow, expand **Schemas**, and then select **\<Select from referenced assembly\>**.  
  
6.  In the Select Artifact Typedialog box, select **Microsoft.Solutions.BTARN.Schemas.RNPIPs** in the left pane, select **_3A2PriceAndAvailabilityQueryMessageGuideline_v1_3** in the right pane, and then click **OK**.  
  
7.  Repeat steps 3 through 6 to create all the message types for the solution using the following information:  
  
    |Identifier|Assembly|Message Type|  
    |----------------|--------------|------------------|  
    |PIP3A2ResponseMessage|Microsoft.Solutions.BTARN.<br />Schemas.RNPips|_3A2PriceAndAvailability<br />ResponseMessageGuideline_v1_3|  
    |Contoso3A2ResponseMessage|ContosoPriceAndAvailability|rootPriceResponse|  
    |Contoso3A2RequestMessage|ContosoPriceAndAvailability|rootPriceRequest|  
  
8.  You have finished creating the message types for the solution.  
  
### To create new variables  
  
1.  In Orchestration View, right-click **Variables,** and then click **New Variable**.  
  
2.  In the Properties window, in the **Identifier** box, type **contosoResponseXML**.  
  
3.  In the **Type** box, select **\<.NET Class\>** from the drop-down list.  
  
4.  In the Select Artifact Type dialog box, in the left pane, under the **Current Project** and **References** nodes, select **System.Xml**, select **XmlDocument** from the list in the right pane, and then click **OK**.  
  
5.  In **Orchestration View**, click **Variables**,and then click **New Variable**.  
  
6.  In the Properties window, in the **Identifier** box, type **submitMessage**.  
  
7.  In the **Type** box, select **\<.NET Class\>** from the drop-down list.  
  
8.  In the Select Artifact Type dialog box, in the left pane, expand **Current Project** and **References** nodes, select **Microsoft.Solutions.BTARN.Shared**, select **SubmitRNIF** from the list in the right pane, and then click **OK**.  
  
### To change the orchestration filter expression  
  
1.  In Orchestration Designer, select the **ReceiveFromPublicProcessResponder** shape.  
  
2.  In the Properties window, in the **Filter Expression** box, click the value box, and then click the ellipsis button (**...**) to open the Filter Expression dialog box.  
  
3.  In the Filter Expression dialog box, in the **Group By** section, click the **OR** value on the first line, and then select **AND** from the drop-down list.  
  
4.  In the Filter Expression dialog box, click **Click here to add a new row**, and then select **Microsoft.Solutions.BTARN.GlobalSchemas.SCPIPCode** from the drop-down list.  
  
5.  In the same row, click **Value**, and then type in **"3A2"**.  
  
6.  In the same row, click **AND** in the **Group By** box, and then select **OR** from the drop-down list.  
  
7.  In the Filter Expression dialog box, select the row that you just created, and then click the up arrow button once to move the row up once.  
  
8.  Click **Click here to add a new row**, and then select **Microsoft.Solutions.BTARN.GlobalSchemas.SCPIPCode** from the drop-down list.  
  
9. In the same row, click **Value**, and then type in **"3A2"**.  
  
10. Click OK.  
  
### To modify the business process workflow  
  
1. Drag a **Message Assignment** shape from the Toolbox to the design surface and drop it under the **ReceiveFromPublicProcessResponder** shape. Select the **ConstructMessage_1** shape that was created and in the **Properties** window, in the **Name** box, type **ConstructPIP3A2RequestMessage**.  
  
2. Drag a **Transform** shape to the design surface and drop it under the **ConstructPIP3A2RequestMessage** shape. Select the **ConstructMessage_1** shape that was created and in the **Properties** window, in the **Name** box, type **ConstructContoso3A2RequestMessage**.  
  
3. Drag a **Send** shape to the design surface and drop it under the **ConstructContoso3A2RequestMessage** shape.  
  
4. Drag a **Receive** shape to the design surface and drop it under the **Send_1** shape.  
  
5. On the orchestration design surface, click an empty area.  
  
6. In the Properties window, select the **Transaction Type** property, and then click **Long Running**.  
  
7. Drag a **Scope** shape to the design surface and drop it under the **Receive_1** shape.  
  
8. In the Properties window, from the **Transaction Type** property drop-down list, select **Atomic** for the **Scope** shape.  
  
9. Drag a **Call Rules** shape to the design surface and drop it on the label that says **Drop a shape from the toolbox here** inside the **Scope** shape. In the Properties window for the **Call Rules** shape, in the **Name** box, type **Execute3A2Vocabulary**.  
  
10. Drag a **Transform** shape to the design surface and drop it under the **Scope_1** shape. Click the **ConstructMessage_1** shape. In the Properties window, in the **Name** box, type **Construct3A2ResponseMessage**.  
  
11. Drag an **Expression** shape to the design surface and drop it under the **Construct3A2ResponseMessageTransform** shape.  
  
12. In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **File**, click **Save All** to save the project.  
  
## See Also  
 [Step 6: Configuring Orchestration Shapes (Contoso)](../../adapters-and-accelerators/accelerator-rosettanet/step-6-configuring-orchestration-shapes-contoso.md)