---
title: "Walkthrough: Module 1 - Sending and Receiving Messages with the Windows SharePoint Services Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Windows SharePoint Services, creating sites"
  - "tutorials, Windows SharePoint Services adapters"
  - "Windows SharePoint Services adapter tutorials, receiving messages"
  - "security, Windows SharePoint Services"
  - "creating, Windows SharePoint Services site"
  - "Windows SharePoint Services, security"
  - "Windows SharePoint Services, document libraries"
  - "Windows SharePoint Services adapters, security"
  - "Windows SharePoint Services"
  - "Windows SharePoint Services adapter tutorials, sending messages"
ms.assetid: 6494aef5-bb1d-4a41-8186-1d49625a1013
caps.latest.revision: 41
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Walkthrough: Module 1 - Sending and Receiving Messages with the Windows SharePoint Services Adapter
This walkthrough shows you how to configure Windows SharePoint Services and [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] so you can send and receive a message using the Windows SharePoint Services Adapter and content-based routing (CBR). Content-based routing eliminates the need for message subscription for messages that are deterministically bound to specific ports. It also provides additional flexibility for users who want to route messages based on envelope properties or simply based on receive port configuration properties. For an introduction to the Windows SharePoint Services adapter, see [What Is the Windows SharePoint Services Adapter?](../core/what-is-the-windows-sharepoint-services-adapter.md).  
  
## Prerequisites  
 The following are prerequisites for performing the procedures in this topic:  
  
- You must have a single-server deployment with a complete installation of BizTalk Server running on [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] or [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)].  
  
  For information about using the Windows SharePoint Services adapter in a multiserver deployment, see [Setting Up and Deploying the Windows SharePoint Services Adapter](../core/setting-up-and-deploying-the-windows-sharepoint-services-adapter.md).  
  
## Configure Windows SharePoint Services  
 In this procedure you create a SharePoint top-level Web site that contains three document libraries. The Windows SharePoint Services adapter uses these libraries to move a message from a source library to a destination library. This message is also archived in a document library. This procedure must be done to provide the Windows Sharepoint Services site that is accessed by the Windows Sharepoint Services adapter in this walkthrough and to set user rights to enable access to this site.  
  
#### Create a Windows SharePoint Services site  
  
1. Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **SharePoint Central Administration.**  
  
2. Under **Virtual Server Configuration**, click **Create a top-level Web site**.  
  
3. Under **Virtual Server List**, select the Web site that you installed the Windows SharePoint Services Adapter on. For example, `Default Web Site`.  
  
4. In the **Web Site Address** section, in the **URL name** field, type `WSSAdapterWalkthrough`.  
  
5. In the **Site Collection Owner** section, in the **User name field,** type a user name. This user will be the owner for the Web site and does not need special permissions in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
6. In the **Site Collection Owner** section, in the **E-mail** field, type in an e-mail address.  
  
7. Click **OK**.  
  
8. On the **Top-Level Site Successfully Created** page, click the new top-level Web site you just created. For example, `http://<server_name>/sites/WSSAdapterWalkthrough`.  
  
9. Select the **Team Site** template from the list of templates, and then click **OK**. This will open the Team Web Site Home page.  
  
#### Create a "Source" document library  
  
1.  On the Team Web Site Home page, on the top navigation bar, click **Create**.  
  
2.  Under **Document Libraries**, click **Document Library**.  
  
3.  In the **Name and Description** section, in the **Name field,** type `Source`.  
  
4.  In the **Navigation** section, select **Yes** to display this form library on the Quick Launch bar.  
  
5.  In the **Document Template** section, in the **Document Template** drop-down list, select `None`.  
  
6.  Click **Create**. The document library will be created and you will be redirected to the empty library.  
  
#### Create a "Destination" document library  
  
1.  On the Team Web Site Home page, on the top navigation bar, click **Create**.  
  
2.  Under **Document Libraries**, click **Document Library**.  
  
3.  In the **Name and Description** section, in the **Name field**, type `Destination`.  
  
4.  In the **Navigation** section, select **Yes** to display this form library on the Quick Launch bar.  
  
5.  In the **Document Template** section, in the **Document Template** drop-down list, select `None`.  
  
6.  Click **Create**. The document library will be created and you will be redirected to the empty library.  
  
#### Create an "Archive" document library  
  
1.  On the Team Web Site Home page, on the top navigation bar, click **Create**.  
  
2.  Under **Document Libraries**, click **Document Library**.  
  
3.  In the **Name** and Description section, in the **Name field**, type `Archive`.  
  
4.  In the **Navigation** section, select **Yes** to display this form library on the Quick Launch bar.  
  
5.  In the **Document Template** section, in the **Document Template** drop-down list, select `None`.  
  
6.  Click **Create**. The document library will be created and you will be redirected to the empty library.  
  
7.  Close the `WSSAdapterWalkthrough` Web site.  
  
8.  Close the **SharePoint Central Administration** Web site.  
  
#### Configure Windows security  
  
1.  Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Computer Management**.  
  
2.  In the console tree, expand **Local Users and Groups**, and then click **Groups**.  
  
3.  Right-click the **SharePoint Enabled Hosts** group, click **Add to Group**, and then click **Add**.  
  
4.  In the **Select Users, Computers, or Groups dialog box**, under **Enter the object names to select**, type the name of the account that you configured the BizTalk Server Host Instance to run under, and then click **OK**.  
  
5.  In the console tree, expand **Services and Applications**, and then click **Services**.  
  
6.  Right-click **BizTalk Service BizTalk Group: <BizTalk_Host_Name>**, and then click **Restart**.  
  
    > [!NOTE]
    >  <BizTalk_Host_Name> is the name of your host. By Default, this is `BizTalkServerApplication`.  
  
    > [!NOTE]
    >  Membership does not take effect until the service is restarted.  
  
7.  Close **Computer Management**.  
  
#### Configure SharePoint security  
  
1. Open a Web browser and navigate to the URL of the site you created. For example, `http://<server_name>/sites/WSSAdapterWalkthrough`.  
  
2. On the Team Web Site Home page, on the top navigation bar, click **Site Settings**.  
  
3. Under **Administration**, click **Manage users**.  
  
4. Click **Add Users**.  
  
5. In **Step 1: Choose Users**, type the name of the account that the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Host Instance is running under.  
  
6. In **Step 2: Choose Site Groups**, select the **Reader** and **Contributor** check boxes.  
  
7. Click **Next**.  
  
8. Clear the **Send the following e-mail to let these users now they've been added** check box, and then click **Finish**.  
  
9. Close the `WSSAdapterWalkthrough` Web site.  
  
## Create and configure the BizTalk Server ports  
 In this procedure you will create and configure the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive ports, receive locations, and send ports for the Windows SharePoint Services adapter. These ports are points of entry into and out of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] for documents received and sent by the Windows Sharepoint Services adapter.  
  
#### Create the receive port  
  
1. Click **Start**, **All Programs**, [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration.**  
  
2. Expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, right-click **Receive Ports**, click **New**, and then click **One-way Receive Port…**  
  
3. In the **Receive Port Properties** dialog box, under **General**, type `FromSource` in the **Name** field.  
  
4. Click **OK**.  
  
#### Create the receive location  
  
1.  In the **BizTalk Administration Console**, right-click the **Receive Locations** node, click **New**, and then click **One-way Receive Location**.  
  
2.  In the **Select a Receive Port** dialog box, select `FromSource`, and then click **OK**.  
  
3.  In the **Receive Location Properties** dialog box, under **General**, type `SourceLocation` in the **Name** field.  
  
4.  In the **Transport** section, in the **Type** drop-down list, select `Windows``SharePoint``Services`.  
  
5.  Click **Configure** to configure the Windows SharePoint Services adapter properties.  
  
6.  In the **Adapter Web Service Port** property, type the port number of the virtual server where the Windows SharePoint Services adapter Web service was installed. By default, this is port 80.  
  
7.  Type `Archive` in the **Archive Location** property.  
  
8.  Type `10` in the **Polling Interval** property.  
  
9. Type the URL to your SharePoint site in the **ShareP**oint Site Url property. For example, `http://<server_name>/sites/WSSAdapterWalkthrough`.  
  
10. Type `Source` for the **Source Document Library** property.  
  
11. Click **OK**.  
  
12. In the **Receive Location Properties** dialog box, select `BizTalkServerApplication` as the **Receive handler**.  
  
13. In the **Receive pipeline** drop-down list, select `PassThruReceive`.  
  
14. Click **OK**.  
  
#### Create the send port  
  
1.  In the **BizTalk Administration Console**, right-click the **Send Ports** node, click **New**, and then click **Static One-way Send Port**.  
  
2.  In the **Send Port Properties** dialog box, under **General**, type `SendToDestination` in the **Name** field.  
  
3.  In the **Transport** section, select `Windows SharePoint Services` for the type.  
  
4.  Click **Configure** to configure the Windows SharePoint Services adapter properties.  
  
5.  In the **Adapter Web Service Port** property, type the port number of the virtual server where the Windows SharePoint Services adapter Web service was installed. By default, this is port 80.  
  
6.  Type in `Destination` for the **Destination Folder** property.  
  
7.  Type in `PurchaseOrder1-%MessageID%.xml` for the **Filename** property.  
  
8.  Set the **Overwrite** property to `Yes`.  
  
9. Type in the URL to your SharePoint site in the **SharePoint Site Url** property. For example, `http://<server_name>/sites/WSSAdapterWalkthrough`.  
  
10. Set the **Microsoft Office Integration** property to `No`.  
  
11. Click **OK**.  
  
12. In the **Send Port Properties dialog box**, in the **Send handler** drop-down list, select `BizTalkServerApplication`.  
  
13. In the **Send pipeline** drop-down list, select `PassThruTransmit`.  
  
14. Click the **Filters** tab.  
  
15. Select `WSS.InListName` in the **Property** field.  
  
16. Select `==` in the **Operator** field.  
  
17. Type `Source` in the **Value** field.  
  
18. Click **OK**.  
  
## Enable and start the receive location and receive port  
 In these procedures you enable the receive location and start the receive port. This procedure must be completed to allow the Windows Sharepoint Services adapter to send and receive messages through the specified send port and receive location.  
  
#### Enable the receive location  
  
1.  In the **BizTalk Administration Console**, click the **Receive Locations** node.  
  
2.  Right-click `SourceLocation`, and then click **Enable**.  
  
#### Start the send port  
  
1.  In the **BizTalk Administration Console**, click the **Send Ports** node.  
  
2.  Right-click `SendToDestination`, and then click **Start**.  
  
3.  Close the **BizTalk Administration Console**.  
  
## Sending a message through the system  
 In this procedure you create an XML document and upload it to the Windows SharePoint Services Web site. The Windows SharePoint Services adapter will take that message, archive it in the Archive document library, and then send it to the Destination document library. This procedure demonstrates how a document flows from a Sharepoint web site, through [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and to a Sharepoint Services Web site using the Windows Sharepoint Services adapter.  
  
#### Create a working directory  
  
-   Create a directory on your computer called **WSSAdapterWalkthrough**. For example, `C:\WSSAdapterWalkthrough`.  
  
#### Create an XML file  
  
1.  Click **Start**, point to **All Programs**, point to **Accessories**, and then click **Notepad.**  
  
2.  Type the following:  
  
    ```  
    <?xml version="1.0"?>  
    <PurchaseOrder>  
        <ID>1001</ID>  
        <FirstName>John</FirstName>  
        <LastName>Doe</LastName>  
        <Amount>750</Amount>  
    </PurchaseOrder>  
    ```  
  
3.  Save the file in your working directory as `PurchaseOrder1.xml`. For example, `C:\WSSAdapterWalkthrough\PurchaseOrder1.xml`.  
  
#### Upload the XML file  
  
1. Open a Web browser and navigate to the URL of the site you created in the last task. For example, `http://<server_name>/sites/WSSAdapterWalkthrough`.  
  
2. On the left side, under **Documents**, click **Source**.  
  
3. Click **Upload Document**.  
  
4. In the **Name** box, type or browse to the XML file you created above. For example, `C:\WSSAdapterWalkthrough\PurchaseOrder1.xml`, and then click **Save and Close**. You should now be able to see the file in the list.  
  
5. Refresh the browser window. The `PurchaseOrder1.xml` file will no longer be listed in this library.  
  
   > [!NOTE]
   >  You may have to refresh the browser a few times since the polling interval is set at 10 seconds.  
  
6. On the top navigation bar, click **Documents and Lists**.  
  
7. Under **Document Libraries**, click **Destination**.  
  
8. In the Destination Document Library, you will now see your message listed. You will also find a copy archived in the Archive Document Library.  
  
   > [!NOTE]
   >  If the message does not appear in the Destination Document Library, refer to "Troubleshooting the Windows SharePoint Services Adapter" in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.  
  
## Summary  
 In this walkthrough you have seen how to configure Windows SharePoint Services and [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] so you can send and receive a message using the Windows SharePoint Services adapter and content-based routing (CBR).  
  
## Next Steps  
 Now that you have completed this walkthrough, perform the [Walkthrough: Module 2 - Integrating Office with the Windows SharePoint Services Adapter](../core/walkthrough-module-2--integrate-office-with-the-sharepoint-adapter-in-biztalk.md) walkthrough, which expands on the work you have done with this walkthrough and shows you how to integrate Office with the Windows SharePoint Services adapter.  
  
## See Also  
 [What Is the Windows SharePoint Services Adapter?](../core/what-is-the-windows-sharepoint-services-adapter.md)   
 [Windows SharePoint Services Adapter Walkthroughs](../core/windows-sharepoint-services-adapter-walkthroughs.md)