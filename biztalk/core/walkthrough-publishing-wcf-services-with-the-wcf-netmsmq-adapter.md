---
title: "Walkthrough: Publishing WCF Services with the WCF-NetMsmq Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e623b6dc-32e5-467c-bb7d-68b7a75723c1
caps.latest.revision: 46
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Walkthrough: Publishing WCF Services with the WCF-NetMsmq Adapter
  
> [!NOTE]
>  For more information about adapters, see [Adapters in BizTalk Server](../core/adapters-in-biztalk-server.md).  
  
## Introduction
  
 In BizTalk Server, an orchestration can be published as a [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] service. Through a BizTalk receive location, an orchestration can expose a [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] endpoint, which allows it to be called by a [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] client. The **BizTalk WCF Service Publishing Wizard** provides a simple way to expose an orchestration as a receive location.  
  
 The WCF-NetMsmq adapter uses the **NetMsmqBinding** binding to provide support for using Microsoft Message Queuing (also known as MSMQ) as its underlying transport. The client of a [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service sends [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] messages to an MSMQ queue by using the receive location configured to use the WCF-NetMSMQ adapter. The adapter picks up the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] messages from the MSMQ queue, converts them into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] format, and writes them to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MessageBox database.  
  
 This walkthrough shows how a [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] client console application uses the WCF-NetMsmq adapter to communicate with a [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service, hosted in a .NET console application, through an MSMQ message queue. It demonstrates how to publish metadata for a receive location with the BizTalk WCF Service Publishing Wizard. It also shows how to configure a Web application to support publishing metadata.  
  
 After completing this walkthrough, you will understand how to perform the following tasks:  
  
- From within Visual Studio, use the **Deploy** command to deploy BizTalk assemblies to a local instance of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. This creates a BizTalk application that is populated with the assemblies. A BizTalk assembly contains resource information such as orchestrations, pipelines, schemas, and maps to be used in a BizTalk solution.  
  
- From the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, configure a WCF-NetMsmq receive location to host the published [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service.  
  
- From the **BizTalk WCF Service Publishing Wizard**, create the Web application to publish metadata for an existing receive location. This metadata is used by the client that submits messages to the receive location.  
  
## Prerequisites  
 To perform the steps in this sample ensure that your environment installs the following prerequisites:  
  
- Both the computer that builds the assemblies and runs the deployment process, and the computer that runs the sample, require Microsoft Windows Server, .NET Framework, and BizTalk Server.  
  
- The computer used to build the assemblies and run the deployment process requires Microsoft Visual Studio.  
  
- The computer that runs the sample requires the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] Adapters and the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] Administration Tools. These are options to install during setup of Microsoft BizTalk Server.  
  
- On the computers that you use to perform administrative tasks, you must run as a user account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group to configure the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application settings within the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console. This user account must also be a member of the local Administrators group for application deployment, managing host instances, and other tasks that may be required.  
  
- On any computer that requires [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] capability, complete the one-time setup procedure for the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] samples at [http://go.microsoft.com/fwlink/?LinkId=135510](http://go.microsoft.com/fwlink/?LinkId=135510).  
  
- On the computer that runs the sample and imports a binding or an .msi file into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ensure the host is not a trusted host or the import will fail.  
  
- You must download the walkthrough code and extract it to your computer. This walkthrough is a part of the entire [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] Adapter Walkthrough package. You can download the file **WCFAdapterWalkthroughs.exe** from the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Developer Center at [http://go.microsoft.com/fwlink/?LinkId=194140](http://go.microsoft.com/fwlink/?LinkId=194140).  
  
## Build and deploy the BizTalk solution, BizTalkApp  
  
1.  Extract WCFNetMsmqAdapterPublishing.exe to **C:\WCFNetMsmqAdapterPublishing**.  
  
2.  In Visual Studio, open the **WCFNetMsmqAdapterPublishing.sln** file.  
  
3.  In Solution Explorer, expand **BizTalkApp**, and then open **OrderProcess.odx** to review. The sample orchestration receives order request messages, and simply returns the order response messages.  
  
4.  Because the **BizTalkApp** assembly must be installed in the GAC, it will need a strong name key file to complete the deployment process. Right-click the **BizTalkApp** project, and then click **Properties**. On the **Properties** page, click **Signing**, and select **Sign the assembly**. Click the down arrow in the **Choose a strong name key file** drop-down list, click **\<New\>** and enter `keyfile.snk` in the **key file name** textbox. Uncheck **Protect my key file with a password**, and then click **OK**.  
  
5.  Click the **Deployment** tab, and then change the **Server** property if you use a different database server for the BizTalk Management database besides **LOCALHOST**.  Ensure **BizTalk Application** value is set to **WCFNetMsmqAdapterPublishing**. Ensure **Install to Global Assembly Cache** is set to **True**.  
  
6.  In Solution Explorer, right-click the **BizTalkApp**  project and then click **Rebuild**.  
  
7.  In Solution Explorer, right-click **BizTalkApp**, and then click **Deploy**.  
  
## Configure the application  
  
1. Make sure that the Microsoft Message Queuing (MSMQ) component is installed on your computer as follows:  
  
   1.  Click **Start**, right-click **Computer**, and then click **Manage** to open **Server Manager**.  
  
   2.  Expand the **Features** node.  If **Message Queuing** is not installed, right-click **Features**, and select **Add Features**. Check **Message Queuing**, click **Next**, and then click **Install** to install MSMQ on that system.  
  
2. Make sure that the MSMQ message queuing service is started on your computer to be used by the WCF-NetMsmq adapter as follows:  
  
   1.  Click **Start**, point to **Administrative Tools**, and then click **Services**.  
  
   2.  In **Services**, make sure that the **Status** of the **Message Queuing** service is **Started**. If the service is not started, right-click **Message Queuing**, and then click **Start**.  
  
3. Create the target queue that the receive location uses from which the WCF-NetMsmq adapter picks up incoming [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] messages from the clients.  
  
   1.  Click **Start**, point to **Administrative Tools**, and then click **Computer Management**.  
  
   2.  In **Computer Management**, expand **Services and Applications**, expand **Message Queuing**, right-click **Private Queues**, point to **New**, and then click **Private Queue**.  
  
   3.  In the **New Private Queue** dialog box, type `WCFNetMsmqAdapterPublishing` in the **Queue name** text box, select the **Transactional** check box, and then click **OK**.  
  
4. Create a WCF-NetMsmq receive location for the sample application as follows:  
  
   1. Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
   2. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Group**, expand **Applications**, expand **WCFNetMsmqAdapterPublishing**, right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port.**  
  
   3. In the **Receive Port Properties** dialog box, in the **Name** text box, type `WCFNetMsmqAdapterPublishing.ReceivePurchaseOrder`, and then click **OK**.  
  
   4. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, right-click **WCFNetMsmqAdapterPublishing.ReceivePurchaseOrder**, point to **New**, and then click **Receive Location**.  
  
   5. In the **Receive Location Properties** dialog box, in the **Name** text box, type `WCFNetMsmqAdapterPublishing.ReceivePurchaseOrder.NetMsmq`.  
  
   6. In the **Receive Location Properties** dialog box, in the **Transport** section next to **Type**, select **WCF-NetMsmq** from the drop-down list, and then click **Configure**.  
  
   7. In the **WCF-NetMsmq Transport Properties** dialog box, on the **General**  tab, in the **Address (URI)** text box, type `net.msmq://localhost/private/WCFNetMsmqAdapterPublishing`.  
  
   8. In the **WCF-NetMsmq Transport Properties** dialog box, on the **Binding**  tab, make sure that the **Transactional** check box is selected.  
  
      > [!NOTE]
      >  Because you created the target queue as a transactional queue, you must select this check box. If this box is not selected, the receive location will not be enabled because there will be a discrepancy between the transactional requirement of the receive location and that of the underlying MSMQ queue.  
  
   9. In the **WCF-NetMsmq Transport Properties** dialog box, on the **Security**  tab, select **None** from the **Security mode** drop-down list.  
  
      > [!NOTE]
      >  This walkthrough assumes that MSMQ is installed with [!INCLUDE[btsAD](../includes/btsad-md.md)] integration disabled on your computer. The default value, **WindowsDomain**, for the **MSMQ authentication mode** property is available when [!INCLUDE[btsAD](../includes/btsad-md.md)] integration is enabled.  
  
   10. In the **Receive Location Properties** dialog box, click **OK**.  
  
5. Create a FILE send port for the sample application. This port is used to route the response from the purchase order from the service's underlying orchestration.  
  
   1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **WCFNetMsmqAdapterPublishing**, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.  
  
   2. In the **Send Port Properties** dialog box, in the **Name** text box, type `WCFNetMsmqAdapterPublishing.SendPurchaseOrder.File`.  
  
   3. In the **Send Port Properties** dialog box, in the **Transport** section next to **Type**, select **FILE** from the drop-down list, and then click **Configure**.  
  
   4. In the **FILE Transport Properties** dialog box, on the **General** tab, in the **Destination folder** text box, type `C:\WCFNetMsmqAdapterPublishing\Out`, and then click **OK**.  
  
   5. In the **Send Port Properties** dialog box, click **OK**.  
  
6. Specify the host name and bindings for the sample application as follows:  
  
   1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **WCFNetMsmqAdapterPublishing**, expand **Orchestrations**, right-click the sample orchestration, click **Properties**, click **Bindings**, and set **Host** to **BizTalkServerApplication** or another appropriate host.  
  
   2. In the **Orchestration Properties** dialog box, select **WCFNetMsmqAdapterPublishing.ReceivePurchaseOrder** from the **Receive Ports** drop-down list for the **PurchaseOrderRequestPort**.  
  
   3. In the **Orchestration Properties** dialog box, select **WCFNetMsmqAdapterPublishing.SendPurchaseOrder.File** from the **Send Ports/Send Port Groups** drop-down list for the **PurchaseOrderResponsePort**.  
  
   4. In the **Orchestration Properties** dialog box, click **OK** to save the configuration.  
  
## Publish the metadata for the WCF-NetMsmq receive location  
  
1. Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk WCF Service Publishing Wizard**.  
  
2. On the **Welcome to the BizTalk WCF Service Publishing Wizard** page, click **Next**.  
  
3. On the **WCF Service Type** page, select the **Metadata only endpoint (MEX)** check box to publish the metadata for the WCFNetMsmq receive location. Select **WCFNetMsmqAdapterPublishing.ReceivePurchaseOrder.NetMsmq** from the **Publish metadata for receive location** drop-down list, and then click **Next**.  
  
4. On the **Create WCF Service** page, select **Publish BizTalk orchestrations as WCF service**, and then click **Next**.  
  
5. On the **BizTalk Assembly** page, in the **BizTalk assembly file (\*.dll)** text box, click **Browse** to browse to the **C:\WCFNetMsmqAdapterPublishing\BizTalkApp\bin\Development** folder, double-click the assembly containing the sample orchestration to publish, and then click **Next**.  
  
6. On the **Orchestrations and Ports** page, make sure that the **Port: PurchaseOrderRequestPort** node is selected on the page, and then click **Next**.  
  
    The MEX for the receive port will be published and used by the client to submit messages to the receive location.  
  
7. On the **WCF Service Properties** page, in the **Target namespace of WCF service** text box, type a URI that you want this published [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service to use, and then click **Next**. For this walkthrough, leave the default URI, `http://tempuri.org/`.  
  
8. On the **WCF Service Location** page, perform the following actions to specify the location of the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] services to create, and then click **Next**:  
  
   1. In the **Location** text box, type the Web directory name where the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service runs or click **Browse** and select a Web directory. For this walkthrough, leave the default location (http://localhost/<em>\<BizTalk Assembly Name\></em>) in the **Location** text box.  
  
   2. Select the **Allow anonymous access to WCF service** option. This option adds anonymous access to the created virtual directory. This option needs to be selected to allow anonymous authentication for the Web application that this wizard will create.  
  
9. On the **WCF Service Summary** page, click **Create** to create the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service.  
  
10. On the **Completing BizTalk WCF Service Publishing Wizard** page, click **Finish**.  
  
## Configure the Web application hosting the published metadata service  
  
1. Open a command prompt, go to the **C:\inetpub\wwwroot\Microsoft.Samples.BizTalk.WCF.NetMsmqPublishing.BizTalkApp** folder where the **BizTalk WCF Service Publishing Wizard** created the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service. Open the **Web.config** file using Notepad.  
  
2. In Notepad, add the following line inside the **\<system.web\>** element:  
  
   ```  
   <trust level="Full" originUrl="" />  
   ```  
  
   > [!NOTE]
   >  This setting is optional. It grants the ASP.NET application hosting the published [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service access to any resource that is subject to operating system security.  
  
3. Test the published [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service by using Internet Explorer as follows:  
  
   1. Click **Start**, point to **Administrator Tools**, and then click **Internet Information Services (IIS) Manager**.  
  
   2. In IIS Manager, create an application pool within which this service will run that has the correct BizTalk database permissions. Right-click **Application Pools**, click **Add Application Pool**, enter a name for the application pool, and then click **OK**.  
  
   3. Expand **Application Pools**, right-click the application pool you just created, and then select **Advanced Settings**. Under **Process Model** section, enter the account which has access to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases under the **Identity** field.  
  
   4. Expand **Web Sites**, expand **Default Web Site**, and then expand the Web application that the BizTalk WCF Service Publishing Wizard created.  
  
   5. In IIS Manager, in the center pane, click **Content View** to display the files for the application.  
  
   6. Right-click the **Microsoft_Samples_BizTalk_WCF_NetMsmqPublishing_BizTalkApp_OrderProcess_PurchaseOrderRequestPort.svc** service file that the **BizTalk WCF Service Publishing Wizard** created, and then click **Browse**. This opens Internet Explorer to display the **BizTalkServerInstance Service** page indicating that an instance of the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service is running. The page displays a full WSDL address that you can copy and use with the Service Metadata Tool (svcutil.exe), or from within Visual Studio, to retrieve proxy code and a configuration file that can be used to create a client application for the service.  
  
   7. Copy to the Clipboard the command line with the full WSDL address from **BizTalkServerInstance Service** page that Internet Explorer shows in the previous step.  
  
       **svcutil.exe http://localhost/Microsoft.Samples.BizTalk.WCF.NetMsmqPublishing.BizTalkApp/Microsoft_Samples_BizTalk_WCF_NetMsmqPublishing_BizTalkApp_OrderProcess_PurchaseOrderRequestPort.svc?wsdl**  
  
## Build the client application  
  
1. Open a Visual Studio command prompt as Administrator and go to the **C:\WCFNetMsmqAdapterPublishing\WCFClient** folder. This is where you will place the proxy class and application configuration file.  
  
2. Paste the entire svcutil.exe command line containing the full WSDL address that you copied in the previous procedure, and then press ENTER. This creates the proxy class, **BizTalkServiceInstance.cs**, and application configuration file, **output.config**. Keep the command prompt window open for use during the final section.  
  
3. In Visual Studio, in Solution Explorer, right-click **WCFClient**, point to **Add**, and then click **Existing Item**.  
  
4. In the **Add Existing Item** dialog box, browse to the **WCFClient** folder, select **All Files (\*.\*)** in the **Files of type** drop-down list, select the **BizTalkServiceInstance.cs** and **output.config** files, and then click **Add**.  
  
5. Expand **WCFClient**, right-click **output.config**, click **Rename**, and then type `App.config` as the new name.  
  
6. Double-click **Program.cs** to review how to call the published [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service using the proxy class generated by svcutil.exe.  
  
7. Expand **References**, and then make sure that the **WCFClient** project has **System.ServiceModel.dll** referenced.  
  
8. Right-click the **WCFClient** project and select **Build**. Keep Visual Studio open and go to the next section.  
  
## Test the sample solution with the WCF-NetMsmq adapter  
  
1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, right-click the **WCFNetMsmqAdapterPublishing** application, and then click **Start**. In the **Start** dialog box, click **Start**.  
  
2. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **Platform Settings**, expand **Host Instances**, right-click **BizTalkServerApplication** or another appropriate host instance, and then click **Restart**. While this step is not required, it is a good idea to ensure the sample works correctly up to this point.  
  
3. In Visual Studio, on the **Debug** menu, click **Start Without Debugging** to run the WCFClient application. This sends a sample message to the WCF-NetMsmq receive location. You will see the output message below stating the message was sent.  
  
    **Calling the Submit operation on the WCF-NetMsmq receive location**  
  
    **Press any key to close WCF client application**  
  
4. Press any key to close the WCFClient application.  
  
5. In the Visual Studio Command Prompt, go to the **C:\WCFNetMsmqAdapterPublishing\Out** folder, and then make sure the response message that the WCFClient application sent back exists.  
  
6. Double-click the {GUID}.xml file to open it in Internet Explorer and view the **OrderID** value processed by the service.  
  
## See Also  
 [Configure a WCF-NetMsmq Receive Location](../core/how-to-configure-a-wcf-netmsmq-receive-location.md)   
 [WCF Adapter Walkthroughs](../core/wcf-adapter-walkthroughs.md)   
 [Publishing Service Metadata for the WCF Receive Adapters](../core/publishing-service-metadata-for-the-wcf-receive-adapters.md)