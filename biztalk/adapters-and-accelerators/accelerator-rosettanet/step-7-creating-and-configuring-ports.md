---
title: "Step 7: Creating and Configuring Ports | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "private process tutorial, creating ports"
  - "private process tutorial, configuring ports"
ms.assetid: c00344c6-506a-4560-a948-e5fed2b9fd58
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 7: Creating and Configuring Ports
In this step, you create and configure the ports you use to communicate with business processes. Each port has a type, direction, and binding property. These properties establish the direction and pattern of communication, the location of where the message is sent or received, and how the communication occurs.  
  
### To create a logical send port  
  
1.  In Visual Studio, from the Toolbox, drag the **Port** shape to the orchestration design surface and drop it on the **Port Surface** to open the **Port Configuration Wizard**.  
  
2.  On the **Port Configuration Wizard** page, click **Next**.  
  
3.  On the **Port Properties** page, in the **Name** box, type **ContosoSQLReqResponsePort**, and then click **Next**.  
  
4.  On the **Select a Port Type** page, in the **Port Type Name** box, type **ContosoSQLReqResponsePortName**.  
  
5.  For **Communication Pattern**, select **Request-Response**.  
  
6.  For **Access Restrictions**, select **Internal - limited to this project**, and then click **Next**.  
  
7.  On the **Port Binding** page, select **I'll be sending a request and receiving a response**, leave the **Port Binding** option set to **Specify Later**, and then click **Next**.  
  
8.  Click **Finish** to create the port.  
  
### To change the variable type for the orchestration ports  
  
1.  In Orchestration View, expand **Types**, expand **Port Types**, expand **ContosoSQLReqResponsePortName**, expand **Operation_1**, and then select **Request**.  
  
2.  In the Properties window, select the **Message Type** property, expand **Schemas** and then click **\<Select from referenced assembly>**.  
  
3.  In the Select Artifact Type dialog box, click **ContosoPriceAndAvailability**.  
  
4.  In the right pane, select **rootPriceRequest**, and then click **OK**.  
  
5.  In Orchestration View, under **Operation_1**, select **Response** for the **ContosoSQLReqResponsePortName** port type.  
  
6.  In the Properties window, select the **Message Type** property, expand **Schemas** and then click \<**Select from referenced assembly>**.  
  
7.  In the **Select Artifact Type** dialog box, click **ContosoPriceAndAvailability**.  
  
8.  In the right pane, select **rootPriceResponse**, and then click **OK**.  
  
### To connect the ports to the Receive shapes  
  
1.  On the orchestration design surface, select the **Send_1** shape.  
  
2.  In the Properties window, select the **Message** property, and then select **Contoso3A2RequestMessage** from the drop-down list.  
  
3.  Connect the **ContosoSQLReqResponsePort** by selecting the green handle next to the **Request** label and dragging it to the green handle on the **Send_1** shape.  
  
4.  On the orchestration design surface, select the **Receive_1** shape.  
  
5.  In the Properties window, select the **Message** property, and then select **Contoso3A2ResponseMessage** from the drop-down list.  
  
6.  Connect the **ContosoSQLReqResponsePort** by selecting the green handle next to the **Response** label and dragging it to the green handle on the **Receive_1** shape.  
  
7.  In the **File** Menu, click **Save All**.  
  
## See Also  
 [Step 8: Building and Deploying the Contoso Orchestration](../../adapters-and-accelerators/accelerator-rosettanet/step-8-building-and-deploying-the-contoso-orchestration.md)