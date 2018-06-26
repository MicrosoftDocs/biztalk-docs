---
title: "Walkthrough: Publishing WCF Services with the WCF-BasicHttp Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tutorials, publishing"
  - "WCF adapters, tutorials"
  - "publishing, WCF services"
  - "WCF-BasicHttp adapters, tutorials"
  - "publishing, tutorials"
  - "WCF services, publishing"
  - "tutorials, WCF adapters"
ms.assetid: 43b76215-9cb0-47ab-a085-c4cf265410f9
caps.latest.revision: 72
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Walkthrough: Publishing WCF Services with the WCF-BasicHttp Adapter
## Introduction  
 This walkthrough publishes a [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] service as a BizTalk orchestration by using the BizTalk WCF Service Publishing Wizard and the WCF-BasicHttp adapter. A BizTalk orchestration appears to an external client, such as another Web service or [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] application, as a [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service by exposing a [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] endpoint using the WCF-BasicHttp adapter. The WCF-BasicHttp adapter consists of both a send adapter and a receive adapter. In this sample you will use only the receive side of this adapter to receive WCF service requests through the HTTP or HTTPS protocol from [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] client applications.  
  
 The WCF-BasicHttp adapter uses the **BasicHttpBinding** binding to provide a transport/protocol stack implementation compatible with the initial release of Web services to serve as a bridge between [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] functionality. It provides communication with legacy ASMX-based Web services and clients that conform to the WS-I Basic Profile 1.1, using either the HTTP or HTTPS transport with text encoding. Using the WCF-BasicHttp adapter you will not be able to take advantage of advanced Web communication features that are supported by WS-* protocols. If you need to do that, use the WCF-WSHttp adapter.  
  
 This walkthrough shows you how to create a WCF-BasicHttp receive location to publish an orchestration as a [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service.  You will configure Internet Information Services (IIS) to provide isolated hosting of that [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service.  A client application calls the published [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] orchestration as an example of how an external client might call the published [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service over the Internet to use its functionality.  
  
 After completing this walkthrough, you will understand how to perform the following tasks:  
  
- From within Visual Studio, use the **Deploy** command to deploy the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service in the form of a BizTalk orchestration inside a BizTalk assembly to a local instance of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Deployment from Visual Studio creates a BizTalk application that is populated with the assemblies containing resources such as orchestrations, pipelines, schemas, and maps to be used in the BizTalk solution.  
  
- After it is deployed, the BizTalk orchestration is available for configuration and control through the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console. In this walkthrough you will configure the WCF-BasicHttp receive location to accept incoming messages sent to the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service that the BizTalk [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] Service Publishing Wizard creates. The receive location is hosted by the BizTalk isolated host in IIS, and acts as a [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service to get to the incoming requests.  
  
> [!NOTE]
>  In this walkthrough, you will use the BizTalk WCF Publishing Wizard and/or BizTalk Web Service Publishing Wizard to publish BizTalk orchestrations and schemas as [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] services with the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] adapters. To publish orchestrations and schemas as Web services with the SOAP adapter, you use the **BizTalk WCF Publish Wizard** and/or **BizTalk Web Services Publishing Wizard**.  
  
## Prerequisites  
 To perform the steps in this sample ensure that your environment installs the following prerequisites:  
  
- Both the computer that builds the assemblies and runs the deployment process, and the computer that runs the sample, require Microsoft Windows Server 2008 SP2 and/or Windows Server 2008 R2, Microsoft .NET Framework 4, and Microsoft BizTalk Server.  
  
- The computer used to build the assemblies and run the deployment process requires Microsoft Visual Studio.  
  
- The computer that runs the sample requires the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] Adapters and the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] Administration Tools. These are options to install during setup of Microsoft BizTalk Server.  
  
- On the computers that you use to perform administrative tasks, you must run as a user account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group to configure the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application settings within the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console. This user account must also be a member of the local Administrators group for application deployment, managing host instances, and other tasks that may be required.  
  
- On any computer that requires [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] capability, complete the one-time setup procedure for the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] samples at [http://go.microsoft.com/fwlink/?LinkId=135510](http://go.microsoft.com/fwlink/?LinkId=135510).  
  
- On the computer that runs the sample and imports a binding or an .msi file into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ensure the host is not a trusted host or the import will fail.  
  
- You must download the walkthrough code and extract it to your computer. This walkthrough is a part of the entire [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] Adapter Walkthrough package. You can download the file **WCFAdapterWalkthroughs.exe** from the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Developer Center at [http://go.microsoft.com/fwlink/?LinkId=194140](http://go.microsoft.com/fwlink/?LinkId=194140).  
  
### To deploy the sample BizTalk solution, BizTalkApp  
  
1. Run the self-extracting **WCFBasicHttpReceiveAdapter.exe** file and extract the files into the **C:\WCFBasicHttpReceiveAdapter** folder.  
  
2. In Microsoft Visual Studio, open the **C:\WCFBasicHttpReceiveAdapter\WCFBasicHttpReceiveAdapter.sln** file.  
  
3. The **Microsoft.Samples.BizTalk.WCFBasicHttpReceiveAdapter.BizTalkApp** assembly contains a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration, a map, and two schemas. It must be installed in the GAC and will need a strong name key file for this to occur. Right-click the **BizTalkApp** project and then click **Properties**. On the **Properties** page, click **Signing**, and select **Sign the assembly**. Click the down arrow in the **Choose a strong name key file** drop-down list, click **\<New\>**, and enter `keyfile.snk` in the **key file name** textbox. Uncheck **Protect my key file with a password**, and then click **OK**.  
  
4. In Solution Explorer, right-click the **BizTalkApp** project, and then click **Rebuild**.  
  
   > [!NOTE]
   >  Do not attempt a **Build Solution**, or to build the **WCFClient** application at this point. The **WCFClient** is not ready to be built at this point in the sample.  
  
5. Expand **BizTalkApp**, and then open **DeliveryProcess.odx** to review. The orchestration takes in a [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] request over HTTP using the WCF-BasicHttp adapter. It modifies the request by using a transformation map and sends out the response again using the same [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] adapter.  
  
   1.  This orchestration has a logical request-response port that will be published with the WCF-BasicHttp adapter. It will be bound to a physical port in a later step.  
  
   2.  Right-click the top node of **DeliveryProcess.odx** in the designer window, and then select **Properties**. Make sure that the **Type Modifier** property of the port type is **Public**.  
  
6. In Solution Explorer, right-click **BizTalkApp**, and then click **Properties**.  
  
   1.  If the BizTalk Management database is not hosted locally, modify the **Server** property if you use a different database server. Click the **Deployment** tab, and then modify the **Server** property to point to the database server.  
  
   2.  Make sure that the **Application Name** property is set to **WCFBasicHttpReceiveAdapter**. This is name of the BizTalk application where the BizTalk solution will be deployed.  
  
   3.  In Solution Explorer, right-click **BizTalkApp**, and then click **Deploy**. If not deploying locally you may need to configure SQL Server to allow remote connections. For more information, see [http://go.microsoft.com/fwlink/?LinkId=194141](http://go.microsoft.com/fwlink/?LinkId=194141).  
  
### To publish the sample orchestration by using the BizTalk WCF Service Publishing Wizard  
  
1. In this step you will take the newly deployed orchestration assembly and publish it as a [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service. To do this, click **Start**, point to **All Programs**, point to **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk WCF Service Publishing Wizard**.  
  
2. On the **Welcome to the BizTalk WCF Service Publishing Wizard** page, click **Next**.  
  
3. On the **WCF Service Type** page, perform the following actions to specify the type of [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service to publish, and the BizTalk endpoints for receiving [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] messages, and then click **Next**:  
  
   1. Select the **Service endpoint** option, which states you will publish a [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service from an orchestration in an assembly. Select **WCF-BasicHttp** from the **Adapter name (Transport type)** drop-down list.  
  
   2. Select the **Enable metadata endpoint** check box to make the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] receive location hosted by IIS publish its [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service metadata. Selecting this check box sets the **httpGetEnabled** attribute of the \<**serviceMetadata**\> element to `true` in Web.Config. This metadata is retrieved when an HTTP/GET request asks for it. Later you will use the SvcUtil.exe tool to obtain this data to generate a proxy class for the client code to use to call the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service.  
  
   3. Select the **Create BizTalk receive locations in the following application** option to create the receive ports and locations corresponding to each generated .svc file for the WCF-BasicHttp adapter. Choose the BizTalk application name, **WCFBasicHttpReceiveAdapter**, where the receive ports and locations will be generated, and then click **Next**.  
  
       The wizard creates a binding file, Binding.XML, to represent associated receive locations. This file is located in the Web directory and later can be manually imported through the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
      > [!NOTE]
      >  If you do not select a deployed BizTalk application here the default application will be selected.  
  
4. On the **Create WCF Service** page, select **Publish BizTalk orchestrations as WCF service**, and then click **Next**. This will publish the orchestration specified in the next step as a [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service.  
  
5. Select the assembly containing the orchestration to be published. On the **BizTalk Assembly** page, in the **BizTalk assembly file (\*.dll)** text box, click **Browse** to browse to the **C:\WCFBasicHttpReceiveAdapter\BizTalkApp\bin\Development** folder, double-click the **Microsoft.Samples.BizTalk.WCFBasicHttpReceiveAdapter.BizTalkApp** assembly containing the sample orchestration to publish, click **Open**, and then click **Next**.  
  
6. On the **Orchestrations and Ports** page, make sure that the **Port: DeliveryRequestPort** node is selected on the page, and then click **Next**. Selecting this node means that its corresponding higher-level nodes are selected as well. The port will be published with a request-response receive location hosting the WCF-BasicHttp adapter.  
  
7. On the **WCF Service Properties** page, in the **Target** namespace of the **WCF service** text box, type a URI that you want this published [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service to use, and then click **Next**. For this walkthrough, leave the default URI, "**<http://tempuri.org/>"** in the Target namespace of the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service text box.  
  
8. On the **WCF Service Location** page, perform the following actions to specify the location of the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] services to create, and then click **Next**:  
  
   1. In the **Location** text box, type the Web directory name where the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service runs, or click **Browse** and select the Web directory. For this walkthrough, since the assembly name is the same as the virtual directory, leave the default location (**<http://localhost/Microsoft.Samples.BizTalk.WCFBasicHttpReceiveAdapter.BizTalkApp>**) in the **Location** text box.  
  
   2. Select the **Allow anonymous access to WCF service** option, and then click **Next**. This option allows anonymous access to the created virtual directory. Because this walkthrough uses the Transport security mode with no authentication, this option needs to be selected to allow anonymous authentication for the Web application that this wizard will create.  
  
9. On the **WCF Service Summary** page, click **Create** to create the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service. This step creates a receive port for the specified orchestration available through the specified Web directory.  
  
10. On the **Completing BizTalk WCF Service Publishing Wizard** page, click **Finish**.  
  
### To enable the sample BizTalk application  
  
1. Click **Start**, point to **All Programs**, point to **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **Applications**, expand **WCFBasicHttpReceiveAdapter**, expand **Orchestrations**, right-click the **DeliveryProcess** orchestration, click **Properties**, and then configure the binding information as follows:  
  
   1. In the **Orchestration Properties** dialog box, click **Bindings**, and then set **Host** to **BizTalkServerApplication**.  
  
   2. In the **Orchestration Properties** dialog box, select a receive port for the **DeliveryRequestPort** to bind. For this walkthrough, select the receive port that the BizTalk [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] Service Publishing Wizard created in the previous procedure, and then click **OK**.  
  
3. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, right-click **WCFBasicHttpReceiveAdapter**, click **Start**, and then click **Start** in the **Start Application** dialog box.  
  
### To configure the Web application hosting the published WCF service  
  
1. Click **Start**, point to **Administrator Tools**, and then click **Internet Information Services (IIS) 7.0 Manager**.  
  
2. In IIS Manager, expand **Sites**, expand **Default Web Site**, and then expand the Web application **Microsoft.Samples.BizTalk.WCFBasicHttpReceiveAdapter.BizTalkApp** that the **BizTalk WCF Service Publishing Wizard** created.  
  
3. Create an application pool within which this service will run. Right-click **Application Pools**, click **Add Application Pool**, enter a name for the application pool, and then click **OK**.  
  
4. Expand **Application Pools**, right-click the application pool you just created, and then select **Advanced Settings**. Under **Process Model** section, enter the account which has access to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases under the **Identity** field.  
  
5. In IIS Manager, click **Content View**.  In the right pane, right-click the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service .svc file that the **BizTalk WCF Service Publishing Wizard** created, and then click **Browse**. This opens Internet Explorer to display a page that indicates you have successfully created a running [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service. The page also includes a full WSDL address that you can copy and use with the Service Metadata Tool (svcutil.exe) to retrieve proxy code and a configuration file that can be used to create a client application for the service.  
  
6. Copy to the Clipboard the SvcUtil.exe command line with the full WSDL address on the page that Internet Explorer displayed in the previous step.  
  
### To create the proxy class for the sample WCF client application, WCFClient  
  
1. Create a proxy class so the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] client sample application can call into the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service. While a proxy is not required, to manually write the code is very complex so creating a proxy is recommended. Open a **Visual Studio Command Prompt** and go to the **C:\WCFBasicHttpReceiveAdapter\WCFClient** folder where you will place the proxy class and application configuration file.  
  
2. Paste the **svcutil.exe** command line with the full WSDL address that you copied in the previous procedure, and then hit **Enter** to create the proxy class and application configuration file. This command line creates **BizTalkServiceInstance.cs** for the proxy class and **output.config** for the application configuration file.  
  
3. In Visual Studio, in Solution Explorer, right-click **WCFClient**, point to **Add**, and then click **Existing Item**.  
  
4. In the **Add Existing Item** dialog box, browse to the **WCFClient** folder, select **All Files (\*.\*)** in the **Files of type** drop-down list, select the **BizTalkServiceInstance.cs** and **output.config** files, and then click **Add**.  
  
5. For the **WCFClient** project, expand **References**, and then make sure that the **WCFClient** project has **System.ServiceModel** as one of its references.  
  
6. Expand the **WCFClient** project, right-click **output.config**, click **Rename**, and then type **App.config** for the new name.  
  
7. Double-click **Program.cs** to review how to call the published [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service using the proxy class generated by **Svcutil.exe**. Calls to instantiate and invoke a [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service appear to be local calls in the simplicity of coding using the **Microsoft_Samples_BizTalk_WCFBasicHttpReceiveAdapter_BizTalkApp_DeliveryProcess_DeliveryRequestPortClient** class. There is no additional code needed to make a call to a remote [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service.  
  
8. In Visual Studio, on the **Debug** menu, click **Start Without Debugging** to run WCFClient. The client code creates a DeliveryItem message and makes a call to the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service, passing in the Address, ProductID, and Amount.  
  
   ```  
   DeliveryItem deliveryRequestItem = new DeliveryItem();  
   deliveryRequestItem.Address = "One Microsoft Way";  
   deliveryRequestItem.ProductID = "00A120c";  
   deliveryRequestItem.Amount = "300";  
   DeliveryRequestPortClient deliveryProcessClient = new DeliveryRequestPortClient("BasicHttpBinding_ITwoWayAsync");  
   DeliveryItem1 deliveryConfirmation = deliveryProcessClient.Submit(deliveryRequestItem);  
   ```  
  
    If the client successfully receives the response message back from the published [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service, it displays the delivery confirmation number (a concatenation of the ProductID and Address) in the response message.  
  
    **Submit operation called with deliveryRequestItem**  
  
    **Delivery confirmation number sent back: 00A120c300One Microsoft Way**  
  
    **Press any key to continue . . .**  
  
## See Also  
 [How to Use the BizTalk WCF Service Publishing Wizard to Publish Orchestrations as WCF Services](../core/publish-orchestrations-as-wcf-services--biztalk-wcf-service-publishing-wizard.md)