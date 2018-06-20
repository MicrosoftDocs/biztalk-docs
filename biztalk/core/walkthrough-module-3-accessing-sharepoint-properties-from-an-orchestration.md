---
title: "Walkthrough: Module 3 - Accessing SharePoint Properties from an Orchestration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "orchestrations, Windows SharePoint Services adapters"
  - "tutorials, Windows SharePoint Services adapters"
  - "Windows SharePoint Services adapters, orchestrations"
  - "Windows SharePoint Services adapter tutorials, accessing SharePoint properties"
ms.assetid: 310c4002-3416-44c6-b409-1d5467063e28
caps.latest.revision: 45
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Walkthrough: Module 3 - Accessing SharePoint Properties from an Orchestration
This walkthrough is a continuation of [Walkthrough: Module 2 - Integrating Office with the Windows SharePoint Services Adapter](../core/walkthrough-module-2--integrate-office-with-the-sharepoint-adapter-in-biztalk.md) and shows you how to access the Windows SharePoint Services context properties of an incoming message at run time and then determine the destination of that message based on a property using dynamic ports in an orchestration. For an introduction to the Windows SharePoint Services adapter see [What Is the Windows SharePoint Services Adapter?](../core/what-is-the-windows-sharepoint-services-adapter.md).  
  
## Prerequisites  
 The following are prerequisites for performing the procedures in this topic:  
  
- You must have a single server deployment with a complete installation of BizTalk Server running on [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] or [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)].  
  
- You must complete the following walkthroughs: [Walkthrough: Module 1 - Sending and Receiving Messages with the Windows SharePoint Services Adapter](../core/walkthrough-module-1--send-and-receive-messages-with-the-sharepoint-adapter.md) and [Walkthrough: Module 2 - Integrating Office with the Windows SharePoint Services Adapter](../core/walkthrough-module-2--integrate-office-with-the-sharepoint-adapter-in-biztalk.md)  
  
  For information about using the Windows SharePoint Services Adapter in a multi server deployment, see [Setting Up and Deploying the Windows SharePoint Services Adapter](../core/setting-up-and-deploying-the-windows-sharepoint-services-adapter.md).  
  
## Modify the BizTalk project  
 In this procedure you modify the PurchaseOrder schema from [Walkthrough: Module 2 - Integrating Office with the Windows SharePoint Services Adapter](../core/walkthrough-module-2--integrate-office-with-the-sharepoint-adapter-in-biztalk.md). This procedure illustrates how to promote a schema property for easy access in a BizTalk orchestration.  
  
#### Modify the PurchaseOrder.xsd schema  
  
1. Start **Microsoft Visual Studio**.  
  
2. Click **File**, click **Open**, and then click **Project/Solution**.  
  
3. Browse to the `OrderProcess.sln` file, and then click **Open**.  
  
4. In **Solution Explorer**, right-click the `OrderProcessSchema.xsd` file, and then click **Open**.  
  
5. In **BizTalk Editor**, expand `PurchaseOrder`.  
  
6. Right-click `Amount`, click **Promote**, and then click **Quick Promotion**.  
  
7. Click **OK**.  
  
   > [!NOTE]
   >  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] creates a property schema for this in the current project.  
  
8. Save `PurchaseOrder.xsd`.  
  
## Create an orchestration  
 In this procedure you create a new BizTalk orchestration. This procedure creates the orchestration that is used to process a message received by the Windows Sharepoint Services adapter.  
  
#### Add a BizTalk orchestration  
  
1.  In **Solution Explorer**, right-click the `OrderProcess` project, click **Add**, and then click **New Item**.  
  
2.  Under **Categories**, select **Orchestration Files**.  
  
3.  Under **Templates**, select **BizTalk Orchestration**.  
  
4.  Type `MyCompanyOrderProcessing` in the **Name** field, and then click **Add**.  
  
## Create receive information  
 In this procedure you create a new message, receive port, and receive shape for the orchestration. This procedure illustrates how to configure an orchestration to receive a message from [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
#### Create a new message  
  
1.  In **Orchestration View**, right-click **Messages**, and then click **New Message**. This will generate a new message with the name `Message_1`.  
  
2.  Right-click `Message_1`, click **Rename**, and then type `Message_PO`.  
  
3.  Right-click `Message_PO`, and then click **Properties Window**.  
  
4.  In the **Message Type** property, expand **Schemas**, and then select `OrderProcess.OrderProcessSchema` schema.  
  
#### Add a receive port to the orchestration  
  
1.  Under **BizTalk Orchestrations** in the Toolbox, drag a **Port** shape to the Port Surface. The Port Configuration Wizard will start.  
  
2.  On the Welcome screen, click **Next**.  
  
3.  Type `ReceivePurchaseOrder` in the **Name** field, and then click **Next**.  
  
4.  Select **Create a new Port Type**.  
  
5.  Type `PurchaseOrderPT` in the **Port Type Name** field, and then click **Next**.  
  
6.  On the **Port Binding screen**, leave the default values, and then click **Next**.  
  
7.  Click **Finish**.  
  
8.  In **Orchestration View**, under **Port Types**, expand the `PurchaseOrderPT` port type.  
  
9. Right-click `Operation_1`, click **Rename**, and then type `PurchaseOrderOperation`.  
  
#### Add a Receive shape to the orchestration  
  
1.  Under **BizTalk Orchestrations** in the Toolbox, drag a **Receive** shape to the Orchestration.  
  
2.  Right-click the Receive shape, and then click **Properties Window**.  
  
3.  Set the **Activate** property to `True`.  
  
    > [!NOTE]
    >  If the activate property is set to false, you will get the following error: "error X2214: you must specify at least one already-initialized correlation set for a non-activation receive that is on a non-selfcorrelating port"  
  
4.  Type `Receive_PO` in the **Name** field.  
  
5.  In the **Properties Window**, select `Message_PO` for the Message property.  
  
6.  Select `ReceivePurchaseOrder.PurchaseOrderOperation.Request` for the **Operation** property. This will tie the port to the Receive shape in the Orchestration Designer.  
  
## Create send information  
 In this procedure you create a new message, send ports, and decision structure to the orchestration. This procedure illustrates how to configure an orchestration with decision logic and how to configure an orchestration to send a message to a send port.  
  
#### Create a new message  
  
1.  In **Orchestration View**, right-click **Messages**, and then click **New Message**. This will generate a new message with the name `Message_1`.  
  
2.  Right-click `Message_1`, click **Rename**, and then type `Message_Task`.  
  
3.  Right-click `Message_Task`, and then click **Properties Window**.  
  
4.  In the **Message Type** property, expand **Schemas**, and then select `OrderProcess.OrderProcessSchema` schema.  
  
#### Add a send port to the orchestration  
  
1.  Under **BizTalk Orchestrations** in the Toolbox, drag a **Port** shape to the Port Surface. The Port Configuration Wizard will start.  
  
2.  On the Welcome screen, click **Next**.  
  
3.  Type `SendPurchaseOrder` in the **Name** field, and then click **Next**.  
  
4.  Select **Use an existing Port Type**.  
  
5.  Under **Available Port Types**, select `OrderProcess.PurchaseOrderPT`, and then click **Next**.  
  
6.  On the **Port Binding screen**, under **Port direction of communication**, select `I'll always be sending messages on this port`, and then click **Next**.  
  
7.  Click **Finish**.  
  
#### Add a Send shape to the orchestration  
  
1.  Under **BizTalk Orchestrations** in the Toolbox, drag a **Send** shape to the Orchestration Designer. Place it below the `Receive_PO` Receive shape.  
  
2.  Right-click the Send shape, and then click **Properties Window**.  
  
3.  Type `Send_PO` in the **Name** field.  
  
4.  Select `Message_PO` for the **Message** property.  
  
5.  Select `SendPurchaseOrder.PurchaseOrderOperation.Request` for the **Operation** property. This will tie the port to the Send shape in the Orchestration Designer.  
  
#### Add a Decide shape to the orchestration  
  
1.  Under **BizTalk Orchestrations** in the Toolbox, drag a **Decide** shape to the Orchestration Designer. Place it below the `Send_PO` Send shape.  
  
2.  Right-click the Decide shape, and then click **Properties Window.**  
  
3.  Type `NeedsApproval` in the **Name** field.  
  
4.  In Orchestration Designer, click **Rule_1** on the Decide shape.  
  
5.  In the Properties Windows, type `ApprovalRequired` for the **Name** property.  
  
6.  Click the **Expression** property field, and then click the ellipsis (**…**) button.  
  
7.  In the BizTalk Expression Editor, type or copy the following:  
  
    ```  
    Message_PO(OrderProcess.PropertySchema.Amount) > 1000  
    ```  
  
8.  Click **OK**.  
  
#### Add another send port to the orchestration  
  
1.  Under **BizTalk Orchestrations** in the Toolbox, drag a **Port** shape to the Port Surface. The Port Configuration Wizard will start.  
  
2.  On the Welcome screen, click **Next**.  
  
3.  Type `SendToTasksList` in the **Name** field, and then click **Next**.  
  
4.  Select **Use an existing Port Type**.  
  
5.  Under **Available Port Types**, select `OrderProcess.PurchaseOrderPT`, and then click **Next**.  
  
6.  On the **Port Binding screen**, under **Port direction of communication**, select `I'll always be sending messages on this port`.  
  
7.  Under **Port binding**, select `Dynamic`, and then click **Next**.  
  
8.  Click **Finish**.  
  
#### Add a Send shape to the Decide shape  
  
1.  Under **BizTalk Orchestrations** in the Toolbox, drag a **Send** shape to the Orchestration Designer. Place it below the `ApprovalRequired` shape.  
  
2.  Right-click the Send shape, and then click **Properties Window**  
  
3.  Type `CreateApprovalTask` in the **Name** field.  
  
4.  Select `Message_Task` for the **Message** property.  
  
5.  Select `SendToTasksList.PurchaseOrderOperation.Request` for the **Operation** property. This will tie the port to the Send shape in the Orchestration Designer.  
  
## Create an expression  
 In this procedure you add an Expression shape to your solution which assigns the Tasks path value to a variable. This procedure illustrates how to add logic to an orchestration to modify the properties of a dynamic send port.  
  
#### Create a new expression  
  
1.  Under **BizTalk Orchestrations** in the Toolbox, drag an **Expression** shape before the `CreateApprovalTask` Send shape.  
  
2.  Right-click the Expression shape, and then click **Properties Window.**  
  
3.  Type `SetPortDestination` in the **Name** field.  
  
4.  Click the **Expression** property field, and then click the ellipsis (**…**) button.  
  
5.  In the **BizTalk Expression Editor**, type the following:  
  
    ```  
    SendToTasksList(Microsoft.XLANGs.BaseTypes.Address) = "wss://localhost/sites/WSSAdapterWalkthrough/Lists/Tasks/";  
    ```  
  
6.  Click **OK**.  
  
## Construct a new message  
 In this procedure you add a Construct shape to the solution which will construct a new instance of a message type within the orchestration. This procedure illustrates how to create a new message that is a copy of the inbound message and then modify the context properties of the new message. This step is required because messages are immutable in BizTalk; that is, once you have constructed it, you cannot modify the original.  
  
#### Add a Construct Shape  
  
1.  Under **BizTalk Orchestrations** in the Toolbox, drag a **Construct Message** shape before the `SetPortDestination` Expression shape.  
  
2.  Right-click the Construct Message shape, and then click **Properties Window.**  
  
3.  Type `ConstructTaskMessage`in the **Name** field.  
  
4.  Select `Message_Task` for the **Messages Constructed** property.  
  
5.  Under **BizTalk Orchestrations** in the Toolbox, drag a **Message Assignment** shape into the `ConstructTaskMessage`**Construct Message** shape.  
  
6.  In the **Properties Window**, type `InitTaskMessage` in the **Name** field.  
  
7.  Click the **Expression** property field, and then click the ellipsis (**…**) button.  
  
8.  In the **BizTalk Expression Editor**, type or copy the following:  
  
    ```  
    Message_Task = Message_PO;  
    Message_Task(WSS.ConfigOverwrite) = "no";  
    Message_Task(WSS.ConfigNamespaceAliases)= "orchns='http://OrderProcess.PurchaseOrder'";  
    Message_Task(WSS.ConfigPropertiesXml) = "<ConfigPropertiesXml><PropertyName1>Title</PropertyName1><PropertySource1>Approve %XPATH=//orchns:PurchaseOrder/orchns:PurchaseOrderID%</PropertySource1><PropertyName3>Status</PropertyName3><PropertySource3>Not Started</PropertySource3><PropertyName4>Priority</PropertyName4><PropertySource4>(1) High</PropertySource4></ConfigPropertiesXml>";  
    ```  
  
    > [!IMPORTANT]
    >  These values supplied for these context properties are case sensitive. When setting configuration values for a dynamic port with context properties you must ensure that you use the proper case or an error will occur when BizTalk attempts to route the document to the designated send port.  
  
9. Click **OK**.  
  
10. Click **File**, and then click **Save All**.  
  
## Build the BizTalk project  
 In this procedure you build and deploy the BizTalk project. This step is required to create and deploy the assembly that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses at runtime.  
  
#### Build and deploy the solution  
  
1. Click **Build**, and then click **Build OrderProcess**.  
  
2. Click **Build**, and then click **Deploy OrderProcess**.  
  
3. Close Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
## Modify the receive location and send port  
 In this procedure you modify the existing receive location and send port to use XML processing for the pipelines. The receive XML pipeline persists message properties used during orchestration processing and the send XML pipeline persists the message properties that were applied in the orchestration which are subsequently used for message routing.  
  
#### Modify the receive location  
  
1. Click **Start**, point to **All Programs**, point to **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration.**  
  
2. Expand **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration SnapIn**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and then click the **Receive Locations** node.  
  
3. Right-click `SourceLocation`, and then click **Properties**.  
  
4. In the **Receive Location Properties** dialog box, under **General**, select `XMLReceive` for the **Receive pipeline** property.  
  
5. Click **OK**.  
  
#### Modify the send port  
  
1.  Click the **Send Ports** node.  
  
2.  Right-click `SendToDestination`, and then click **Properties**.  
  
3.  In the **Send Port Properties** dialog box, under **General**, select `XMLTransmit` for the **Send pipeline** property.  
  
4.  Select the **Filters** tab.  
  
5.  Select the existing condition, press DELETE, and then click **OK**.  
  
#### Start a new send port  
  
1.  Click the **Send Ports** node.  
  
2.  Right-click `OrderProcess_1.0.0.0_OrderProcess.MyCompanyOrderProcess_SendToTasksList_<GUID>`, and then click **Start**.  
  
> [!NOTE]
>  You may have to refresh the console if this is not visible.  
  
## Bind the orchestration  
 In this procedure you bind the orchestration to the specified ports. This procedure is required to tie physical ports to the orchestration that you built and deployed.  
  
#### Bind the orchestration  
  
1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, click the **Orchestrations** node.  
  
2. Right-click the `OrderProcess.MyCompanyOrderProcessing` orchestration, and then click **Properties**.  
  
3. Select the **Bindings** tab.  
  
4. Under **Host**, select `BizTalkServerApplication` in the **Host** field.  
  
5. Under **Bindings**, select `FromSource` for the `ReceivePurchaseOrder` Inbound Logical Port.  
  
6. Under **Bindings**, select `SendToDestination` for the `SendPurchaseOrder` Outbound Logical Port.  
  
7. Click **OK**.  
  
8. Right click `OrderProcess.MyCompanyOrderProcessing` orchestration, and then click **Start**.  
  
## Send a message through the system  
 In this procedure you create an InfoPath form and upload it to the Windows SharePoint Services Web site. The Windows SharePoint Services adapter will take that message, archive it in the Archive document library, and then send it to the Destination document library. During the processing of this message, Windows SharePoint Services context properties will be accessed that help determine the destination.  
  
#### Create an InfoPath form to send through the system  
  
1.  Open a Web browser and navigate to the URL of the site you created. For example, `http://<server_name>/sites/WSSAdapterWalkthrough`.  
  
2.  In the Quick Launch menu, click `InfoPathSolutions`.  
  
3.  Click the `PurchaseOrder` file to display the **File Download** dialog box, and then click **Open**. InfoPath will load the form.  
  
4.  In the **Purchase Order ID** field, type `1003`.  
  
5.  In the **Bill To** field, type `John Doe`.  
  
6.  In the **Amount** field, type `1750`.  
  
7.  In the **Purchase Order Date** field, type `1/3/2005`.  
  
8.  Click **Save**.  
  
9. In the **Save As** dialog box, type `http://<server_name>/sites/WSSAdapterWalkthrough/Source`in the **file name** field, and then press ENTER.  
  
10. Type `PurchaseOrder3.xml` in the **file name** field, and then click **Save**.  
  
11. Close InfoPath.  
  
12. In the Web browser, click **Documents and Lists**.  
  
13. Under **Document Libraries**, click **Destination**.  
  
14. In the Destination document library, you will now see your message listed in this library. You will also find a copy archived in the Archive document library.  
  
15. Click **Home**.  
  
16. Under **Lists**, click **Tasks**.  
  
17. In the Tasks list you will see the newly created approval task.  
  
> [!NOTE]
>  Since the amount of the purchase order was over $1,000.00, the task was created.  
  
## Summary  
 In this walkthrough you have seen how to access the Windows SharePoint Services context properties and how to determine the destination of messages going through dynamic ports.  
  
## Next Steps  
 Continue to review the rest of the Windows SharePoint Services adapter section. For more information, see the topics in See Also.  
  
## See Also  
 [What Is the Windows SharePoint Services Adapter?](../core/what-is-the-windows-sharepoint-services-adapter.md)   
 [Windows SharePoint Services Adapter Walkthroughs](../core/windows-sharepoint-services-adapter-walkthroughs.md)