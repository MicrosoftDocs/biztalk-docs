---
title: "Walkthrough: Module 2 - Integrating Office with the Windows SharePoint Services Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Windows SharePoint Services adapters, InfoPath forms"
  - "InfoPath forms, creating"
  - "InfoPath forms, Windows SharePoint Services adapters"
  - "tutorials, Windows SharePoint Services adapters"
  - "Windows SharePoint Services adapter tutorials, integrating Microsoft Office"
  - "Windows SharePoint Services, document libraries"
ms.assetid: 2f81a712-bb20-4c32-bbac-fb438deded38
caps.latest.revision: 48
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Walkthrough: Module 2 - Integrating Office with the Windows SharePoint Services Adapter
This walkthrough is a continuation of [Walkthrough: Module 1 - Sending and Receiving Messages with the Windows SharePoint Services Adapter](../core/walkthrough-module-1--send-and-receive-messages-with-the-sharepoint-adapter.md) and shows you how to integrate Microsoft Office with the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] content-based routing (CBR) application you created. For an introduction to the Windows SharePoint Services adapter see [What Is the Windows SharePoint Services Adapter?](../core/what-is-the-windows-sharepoint-services-adapter.md).  
  
## Prerequisites  
 The following are prerequisites for performing the procedures in this topic:  
  
- You must have a single-server deployment with a complete installation of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
- You must complete the following walkthrough: [Walkthrough: Module 1 - Sending and Receiving Messages with the Windows SharePoint Services Adapter](../core/walkthrough-module-1--send-and-receive-messages-with-the-sharepoint-adapter.md)  
  
  For information about using the Windows SharePoint Services Adapter in a multiserver deployment, see [Setting Up and Deploying the Windows SharePoint Services Adapter](../core/setting-up-and-deploying-the-windows-sharepoint-services-adapter.md).  
  
## Create a BizTalk project  
 In this procedure you create an empty BizTalk project and a schema using the BizTalk Editor. This procedure is required to create the schema for the InfoPath form that is used later.  
  
#### Create a strong name key file  
  
1.  Start **Visual Studio Command Prompt**.  
  
2.  Type `sn -k C:\WSSAdapterWalkthrough\OrderProcess.snk`, and then press **Enter**. The key pair will be written.  
  
3.  Close the command prompt.  
  
#### Create an empty BizTalk project  
  
1.  Start **Microsoft Visual Studio**.  
  
2.  Click **File**, **New**, and then click **Project**.  
  
3.  Under **Project types**, select **BizTalk Projects**.  
  
4.  Under **Templates**, select **Empty BizTalk Server Project**.  
  
5.  Type `OrderProcess` in the **Name** field.  
  
6.  Type the file path to your working directory in the **Location** field. For example, `C:\WSSAdapterWalkthrough\`.  
  
7.  Click **OK**.  
  
#### Associate the key file with the assembly  
  
1.  In Solution Explorer, right-click the `OrderProcess` project, and then click **Properties** to launch the Project Designer.  
  
2.  Click the **Signing** tab.  
  
3.  Select **Sign the assembly** option, click drop-down list for the **Choose a strong name key file** option, and then click **Browse**.  
  
4.  Type `C:\WSSAdapterWalkthrough\OrderProcess.snk`.  
  
5.  Click **Open**.  
  
#### Create an XSD schema by using the BizTalk Editor  
  
1. In Solution Explorer, right-click the `OrderProcess` project, click **Add**, and then click **New Item**.  
  
2. Under **Categories**, click **Schema Files**.  
  
3. Under **Templates**, click **Schema**.  
  
4. Type `OrderProcessSchema` in the **Name** field, and then click **Add**.  
  
5. In the Properties Window for `OrderProcessSchema`, select `Qualified` for the **Element FormDefault** property.  
  
6. In the Properties Window for `OrderProcessSchema`, type `http://OrderProcess.PurchaseOrder` in the **Target Namespace** field.  
  
7. In the **BizTalk Editor**, right-click `Root`, click **Rename**, and then type `PurchaseOrder`.  
  
8. Right-click the **PurchaseOrder** node, click **Insert Schema Node**, then click **Child Field Element**.  
  
9. Name it `PurchaseOrderID`.  
  
10. Create another child field element and name it `BillTo`.  
  
11. Create another child field element and name it `Amount`.  
  
12. In the Properties Window, set the **Data Type** property for `Amount` to xs:unsignedInt.  
  
13. Create another child field element and name it `PurchaseOrderDate`.  
  
14. In the Properties Window, set the **Data Type** property for `PurchaseOrderDate` to xs:dateTime.  
  
15. Click **File**, and then click **Save All**.  
  
16. Close [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
## Create an InfoPath form  
 In this procedure you create another document library and an InfoPath form based on the schema you created in the last procedure. This InfoPath form will be used to submit a document to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
> [!NOTE]
>  This walkthrough requires Microsoft Office InfoPath 2007  
  
#### Create a new document library  
  
1.  Open a Web browser and navigate to the URL of the site you created. For example, `http://<server_name>/sites/WSSAdapterWalkthrough`.  
  
2.  On the top navigation bar, click **Create**.  
  
3.  Under **Document Libraries**, click **Document Library**.  
  
4.  In the **Name and Description** section, type `InfoPathSolutions` in the **Name field**.  
  
5.  In the **Navigation** section, select **Yes** to display this form library on the Quick Launch bar.  
  
6.  In the **Document Template** section, select `None` for the **Document Template**.  
  
7.  Click **Create**. You will be redirected to the empty library you just created.  
  
8.  On the left side, click **Modify Settings and Columns**.  
  
9. Under **Columns**, click **Add a New Column**.  
  
10. Under **Name and Type**, type `Namespace` in the **Name** field.  
  
11. Click **OK**.  
  
12. Close the `WSSAdapterWalkthrough` Web site.  
  
#### Create an InfoPath form based on the OrderProcessSchema schema file  
  
1.  Click **Start**, point to **All Programs**, point to **Microsoft Office**, and then click **Microsoft Office InfoPath 2007**.  
  
2.  In the **Fill Out a Form** dialog box, select **Design a Form.**  
  
3.  In the **Design a Form** task pane, select **New from XML Document or Schema**.  
  
4.  In the **Data Source Wizard**, click **Browse** and select the schema file you created in the last procedure. For example, `C:\WSSAdapterWalkthrough\OrderProcess\OrderProcess\OrderProcessSchema.xsd`.  
  
5.  Click **Next**, and then click **Finish**.  
  
6.  In the **Data Source** task pane, right-click the **PurchaseOrder** node, and then click **Section with Controls**. This will create the form on the template.  
  
7.  Click **File**, click **Save**, and then click **Save**.  
  
8.  In the **Save As** dialog box, type `PurchaseOrder.xsn` in the **File name** field, and then click **Save**.  
  
9. Click **File**, and then click **Publish**.  
  
10. In the **Publishing Wizard**, click **Next**.  
  
11. Select **To a Web Server**, and then click **Next**.  
  
12. Type the path and filename to your `InfoPathSolutions` document library, and then click **Next**. For example, `http://<server_name>/sites/WSSAdapterWalkthrough/InfoPathSolutions/PurchaseOrder.xsn`.  
  
13. Click **Finish**, and then click **Close**.  
  
14. Close Microsoft InfoPath.  
  
## Modify the SharePoint document libraries  
 In this procedure you will update the namespace property for the PurchaseOrder.xsn file and modify the Destination Document Library. This namespace is used as a variable when determining subscribers of published documents for content based routing scenarios.  
  
#### Update the namespace for PurchaseOrder.xsn  
  
1.  Open a Web browser and navigate to the URL of the site you created. For example, `http://<server_name>/sites/WSSAdapterWalkthrough`.  
  
2.  On the left side, under **Documents**, click `InfoPathSolutions`.  
  
3.  Move the pointer over `PurchaseOrder.xsn`, right-click it, and then click **Edit Properties**.  
  
4.  Type `http://OrderProcess.PurchaseOrder` in the **Namespace** field, and then click **Save and Close**.  
  
#### Modify the Destination document library  
  
1.  On the top navigation bar, click **Documents and Lists**.  
  
2.  Under **Document Libraries**, click **Destination**.  
  
3.  On the left side, click **Modify Settings and Columns**.  
  
4.  Under **Columns**, click **Add New Column**.  
  
5.  Under **Name and Type**, type `Partner Name` in the **Column name** field.  
  
6.  Click **OK**.  
  
7.  Close the `WSSAdapterWalkthrough` Web site.  
  
## Modify the send port from walkthrough 1  
 In this procedure you modify the send port from walkthrough 1. This procedure is required to ensure that the document processed in this walkthrough is correctly routed to the send port.  
  
#### Modify the send port  
  
1. Open **BizTalk Server Administration.**  
  
2. Expand **Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and then click the **Send Ports** node.  
  
3. Right-click `SendToDestination`, and then click **Properties**.  
  
4. Under **Transport**, click **Configure**.  
  
5. In the **Filename** field, type `PurchaseOrder2-%XPATH=//pons:PurchaseOrder/pons:PurchaseOrderID%.xml`.  
  
6. In the **Namespace Aliases** field, type `pons="http://OrderProcess.PurchaseOrder"`.  
  
7. In the **Templates Document Library**, type `InfoPathSolutions`.  
  
8. In the **Templates Namespace Column**, type `Namespace`.  
  
9. Select `Yes` for the **Microsoft Office Integration** property.  
  
10. Under **Windows SharePoint Services Integration**, type `Partner Name` in the **Column 01** field.  
  
11. Type `%XPATH=//pons:PurchaseOrder/pons:BillTo%` in the **Column 01 Value** field, click **OK**, and then click **OK** again to exit the **Send Port Properties** dialog box.  
  
#### Restart the send port  
  
1.  In the **BizTalk Administration Console**, click the **Send Ports** node.  
  
2.  Right-click `SendToDestination`, and then click **Unenlist**.  
  
3.  Right-click `SendToDestination`, and then click **Start**.  
  
4.  Close the **BizTalk Administration Console**.  
  
## Send a message through the system  
 In this procedure you create an InfoPath form and upload it to the Windows SharePoint Services Web site. The Windows SharePoint Services adapter will take that message, archive it in the Archive document library, and then send it to the Destination document library. This procedure demonstrates how a document flows from a Sharepoint web site, through [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and to a Sharepoint Services Web site using the Windows Sharepoint Services adapter.  
  
#### Create an InfoPath form to send through the system  
  
1.  Open a Web browser and navigate to the URL of the site you created. For example, `http://<server_name>/sites/WSSAdapterWalkthrough`.  
  
2.  On the left side, under **Documents**, click `InfoPathSolutions`.  
  
3.  Click the `PurchaseOrder` file to display the **File Download** dialog box, and then click **Open**. InfoPath will load the form.  
  
4.  In the **Purchase Order ID** field, type `1002`.  
  
5.  In the **Bill To** field, type `John Doe`.  
  
6.  In the **Amount** field, type `750`.  
  
7.  In the **Purchase Order Date** field, type `1/2/2005`.  
  
8.  Click **Save**.  
  
9. In the **Save As** dialog box, type `http://<server_name>/sites/WSSAdapterWalkthrough/Source`in the **file name** field, and then hit Enter.  
  
10. Type `PurchaseOrder2.xml` in the **file name** field, and then click **Save**.  
  
11. Close Microsoft Office InfoPath.  
  
12. In the Web browser, on the top navigation bar, click **Documents and Lists**.  
  
13. Under **Document Libraries**, click **Destination**.  
  
14. In the Destination document library, you will now see your message listed. You will also find a copy archived in the Archive document library.  
  
15. In the Destination document library, click `PurchaseOrder1.xml`. Note that this XML file is opened in Microsoft Internet Explorer.  
  
16. In the Destination document library, click `PurchaseOrder2.xml`. Note that this XML file is opened in Microsoft Office InfoPath.  
  
> [!NOTE]
>  In the Destination document library, the file name column should contain the value of the PurchaseOrderID field and the Partner Name column should contain the value of the BillTo field.  
  
## Summary  
 In this walkthrough you have seen how to add tighter integration with Microsoft InfoPath using the Windows SharePoint Services Adapter and content-based routing (CBR).  
  
## Next Steps  
 Now that you have completed this walkthrough, perform the [Walkthrough: Module 3 - Accessing SharePoint Properties from an Orchestration](../core/walkthrough-module-3-accessing-sharepoint-properties-from-an-orchestration.md) walkthrough which expands on the work you have done with this walkthrough, integrates an orchestration into the project, and shows you how to access SharePoint properties from within it.  
  
## See Also  
 [What Is the Windows SharePoint Services Adapter?](../core/what-is-the-windows-sharepoint-services-adapter.md)   
 [Windows SharePoint Services Adapter Walkthroughs](../core/windows-sharepoint-services-adapter-walkthroughs.md)