---
title: "Step 7 (On Premises): Create an Orchestration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c0b6d0e-cf00-4eee-9b89-28210bad46f4
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 7 (On Premises): Create an Orchestration
According to the business scenario, after [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives the sales order message from the Service Bus Queue, it needs to check whether the quantity ordered in the message is greater than 100. If the quantity is greater than 100, the message is inserted into the **SalesOrder** table. Otherwise, the message is sent to a shared file location. Northwind achieves this business logic by creating an orchestration. This topic provides step-by-step guidance on how to create the orchestration.  
  
### To add an orchestration to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project  
  
1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] you already created, right-click the project, point to **Add**, and then click **New Item**.  
  
2. In the **New Item** dialog box, select **BizTalk Orchestration**, enter the map name as `OrderProcessing.odx`, and then click **Add**.  
  
## Create Messages for the Orchestration  
 The schema that you generated earlier describes the “types” required for the messages in the orchestration. A message is typically a variable, the type for which defined by the corresponding schema. You must now create messages for the orchestration and link them to schemas you generated earlier. You need to create following three messages:  
  
|Message Name|Corresponds to schema|  
|------------------|---------------------------|  
|Message1_SO_Inbound|This message is an instance of the **ECommerceSalesOrder.xsd** schema.|  
|Message2_SO_Inbound|This message is a copy of the **Message1_SO_Inbound**. As a best practice, you must create a copy of the message and then modify the new message, leaving the original message intact. For more information, see [The BizTalk Server Message](http://msdn.microsoft.com/library/aa560436).|  
|Message1_SO_Outbound|This message is an instance of the **TableOperations.dbo.SalesOrder (Insert)** schema.|  
  
#### To create the messages  
  
1.  Open the **Orchestration View** window of the BizTalk project, if it is not already open. To do so, click **View**, point to **Other Windows**, and then click **Orchestration View**.  
  
2.  In Orchestration View, right-click **Messages**, and then click **New Message**.  
  
3.  Right-click the newly created message, and then select **Properties Window**.  
  
4.  In the **Properties** pane for the **Message_1**, do the following:  
  
    |Property name|Perform action|  
    |-------------------|--------------------|  
    |Identifier|Enter `Message1_SO_Inbound`|  
    |Message Type|From the drop-down list, expand **Schemas**, and then select *OrderProcessingDemo.ECommerceSalesOrder*, where *OrderProcessingDemo* is the name of your BizTalk project. *ECommerceSalesOrder* is the schema for the sales order message received from the Service Bus Queue.|  
  
5.  Repeat the steps to create the messages with following details:  
  
    |Message name||  
    |------------------|-|  
    |Message2_SO_Inbound|-   Set **Identifier** to `Message2_SO_Inbound`<br />-   Set **Message Type** to *OrderProcessingDemo.ECommerceSalesOrder*|  
    |Message1_SO_Outbound|-   Set **Identifier** to `Message1_SO_Outound`<br />-   Set **Message Type** to *OrderProcessingDemo.TableOperation_dbo_SalesOrder.Insert*|  
  
## Add Shapes to the Orchestration  
 Orchestration shapes define the flow of a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application. In this section, you add the required shapes to the orchestration.  
  
#### To add shapes to the orchestration  
  
1.  To start with, you must add a **Receive** shape. This shape receives the incoming sales order message from the Service Bus Queue. Set the following properties on the receive shape.  
  
    1.  Set **Activate** to **True**.  
  
    2.  Set **Message** to **Message1_SO_Inbound**.  
  
    3.  Set **Name** to **ReceiveOrder**.  
  
2.  As mentioned earlier, you must create a copy of the original sales order message that is received into the orchestration.  
  
    1.  Drag-and-drop a **Construct Message** shape under the **ReceiveOrder** shape. Because you use this shape to construct a message of type Message2_SO_Inbound, set the **Messages Constructed** property to **Message2_SO_Inbound**.  
  
    2.  Add a **Message Assignment** shape within the **Construct Message** shape. Double-click the shape to open the Expression Editor, and add the following:  
  
        ```  
        Message2_SO_Inbound = Message1_SO_Inbound; //copy the message  
        Message2_SO_Inbound(*) = Message1_SO_Inbound(*); //copy the context properties on the message  
        ```  
  
         Click **OK**.  
  
3.  According to the business scenario, the message must be sent to different destinations based on the quantity of ordered items. So, you must now extract the quantity value from the incoming sales order message.  
  
    1.  The **Quantity** element in the inbound message (ECommerceSalesOrder.xsd) contains the value of the ordered quantity. You must promote that property so that the element can be used within the expressions in the orchestration. To promote the property, open the **ECommerceSalesOrder.xsd** schema, right-click **Quantity**, point to **Promote**, and then click **Quick Promotions**.  
  
    2.  Create a variable to store the quantity value. To create a variable, from the **Orchestration View**, right-click **Variables**, and then click **New Variable**. Set the following properties for the variable:  
  
        |Property name|Value|  
        |-------------------|-----------|  
        |Identifier|Enter `quantityOrdered`|  
        |Type|Select **Int32**.|  
  
    3.  You must now assign the value in the **Quantity** element to the **quantityOrdered** variable. Drag-and-drop an **Expression Editor** after the **Construct Message** shape. Open the editor and enter the following expression:  
  
        ```  
        quantityOrdered = Message2_SO_Inbound.Quantity;  
        ```  
  
         Click **OK**.  
  
4.  After extracting the order quantity, you now need to create a decision block where you layout two separate paths the message flow takes. You create the decision block in an orchestration by adding a **Decide** shape.  
  
    1.  Drag and drop a **Decide** shape after the **Expression Editor** shape.  
  
    2.  Select the **Rule_1** shape and in the **Properties** window, specify the following:  
  
        |Property name|Value|  
        |-------------------|-----------|  
        |Identifier|Enter `Yes`. **Note:**  The other route is by default named **Else**.|  
        |Expression|Enter `quantityOrdered > 100`.|  
  
         You now have two routes available. If the value in the **quantityOrdered** variable is greater than 100, the message takes the **Yes** route. Otherwise, it takes the **Else** route. You must now define the actions to be performed within each route.  
  
5.  According to the business scenario, if the order quantity is greater than 100, the message must be inserted into the SalesOrder table. So, in the **Yes** route, you must transform the ECommerceSalesOrder.xsd schema to the TableOperations.SalesOrder.Insert schema. You created the Insert schema in the topic [Step 5 (On Premises): Generate the Schema for Inserting a Message inito SalesOrder Table](../core/step-5-generate-the-schema-for-inserting-a-message-into-salesorder-table.md). After transforming the schema, you must send the message to the message out to the SQL Server database table.  
  
    1.  Within the **Yes** route, drag and drop a **Construct Message** shape. Set the **Messages Constructed** property for the shape to **Message1_SO_Outbound**.  
  
    2.  Within the **Construct Message** shape add a **Transform** shape. Double-click the shape to open the **Transform Configuration** dialog box. Do the following:  
  
        1.  Select the **Existing Map** option.  
  
        2.  From the **Fully Qualified Map Name** drop-down, select **OrderProcessingDemo.SalesOrder_SQL**.  
  
        3.  For **Source**, select **Message2_SO_Inbound**.  
  
        4.  For **Destination**, select **Message1_SO_Outound**.  
  
    3.  After the **Construct Message** shape, drag and drop a **Send** shape and set the **Message** property for the shape to `Message1_SO_Outbound`.  
  
6.  According to the business scenario, if the order quantity is less than 100, the message must be sent to a shared file location. So, in the **Else** route you must add a send shape.  
  
    1.  Within the **Else** route, drag and drop a **Send** shape, and set the **Message** property for the shape to `Message2_SO_Inbound`.  
  
        > [!NOTE]
        >  You set the Message to Message2_SO_Inbound because the same message that is received from the Service Bus Queue is sent to the file location, without any processing. Message2_SO_Inbound represents the message that is received by the Service Bus Queue.  
  
## Add Ports to the Orchestration  
 Ports represent the input and output mediums of the message with respect to an orchestration. Messages are consumed by an orchestration using a receive port and are sent out using a send port. In the business scenario, a message is received from one medium (Service Bus Queue) and then sent out to two different locations (SQL Server database or a file share location) based on message processing. So, you must create one receive port and two send ports as part of the orchestration.  
  
#### To add ports  
  
1.  Drag and drop a **Port** shape to the **Port Surface** pane of the **Orchestration Designer** to launch the **Port Configuration Wizard**. On the **Welcome** page, click **Next**.  
  
2.  In the **Port Properties** page, name the port as `ReceiveSO` and then click **Next**.  
  
3.  In the **Select a Port Type** page, select **Create a new port type** option, select the **One-Way** communication pattern, leave the default for access restrictions, and then click **Next**.  
  
4.  In the **Port Binding** page, for the port direction, select **I’ll always be receiving messages on this port**, leave the port biding to the default value, and then click **Next**.  
  
5.  On the last page, click **Finish**.  
  
6.  Repeat the steps to create the two send ports. Specify the following values while creating the ports.  
  
    |Port Name|Properties|  
    |---------------|----------------|  
    |SendToSQL|-   Set **Name** to **SendToSQL**<br />-   Select **Create a new port type**<br />-   Set communication pattern to **One-way**<br />-   Set port direction to **I’ll always be sending messages on this port**|  
    |SendToFile|-   Set **Name** to **SendToFile**<br />-   Select **Create a new port type**<br />-   Set communication pattern to **One-way**<br />-   Set port direction to **I’ll always be sending messages on this port**|  
  
## Connect Ports and Message Shapes  
 You must now connect the ports and the message shapes to complete the orchestration. The orchestration starts when the message is received by the **ReceiveOrder** shape and the orchestration exits when the message is sent out by the two Send shapes. You must use this criterion to connect the ports and the message shapes  
  
#### To connect ports with message shapes  
  
1.  Connect the **ReceiveSO** receive port to the **ReceiveOrder** shape.  
  
2.  Connect the Send shape under the **Yes** route to the **SendToSQL** send port. This denotes that if a message enters this route (**quantityOrdered** > 100), it’ll be sent to the **SalesOrder** table in the SQL Server database.  
  
3.  Connect the Send shape under the **Else** route to the **SendToFile** send port. This denotes that if a message enters this route (**quantityOrdered** <= 100), it’ll be sent to a specified file location.  
  
     The orchestration must resemble the following:  
  
     ![Orchestration](../core/media/bts2010r2-tut1-orch.jpg "BTS2010R2_Tut1_Orch")  
  
## See Also  
 [Tutorial 4: Creating a Hybrid Application Using BizTalk Server 2013](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)