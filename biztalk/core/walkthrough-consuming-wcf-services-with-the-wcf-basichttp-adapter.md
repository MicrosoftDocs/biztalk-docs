---
title: "Walkthrough: Consuming WCF Services with the WCF-BasicHttp Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2d280198-ba55-4937-91c9-19d6d0ed3194
caps.latest.revision: 49
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Walkthrough: Consuming WCF Services with the WCF-BasicHttp Adapter
  
> [!NOTE]
>  For more information about adapters, see [Adapters in BizTalk Server](../core/adapters-in-biztalk-server.md).  
  
## Introduction
  
 In this walkthrough, you will consume a [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] service hosted inside Internet Information Services (IIS) using BizTalk messaging and the WCF-BasicHttp send adapter. This adapter uses the **BasicHttpBinding** binding to provide a transport/protocol stack implementation compatible with earlier versions of Web services to serve as a bridge between Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] functionality. An orchestration can bind to a send port that uses a [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] adapter to call a [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service and leverage its functionality within its logical business processing.  
  
 The WCF-BasicHttp adapter consists of both a send adapter and a receive adapter. In this sample you will use only the send side of this adapter to make WCF service requests through the HTTP protocol to a [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service.  For a Solicit-Response send port, the send adapter sends to a [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service and receives back a result response.  Conversely, a [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] receive adapter allows a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration to be published and called externally by a [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] client application. Refer to the [Publishing WCF Services](../core/publishing-wcf-services.md) for additional information.  
  
 After completing this walkthrough, you will understand how to perform the following tasks:  
  
- From within [!INCLUDE[btsCoName](../includes/btsconame-md.md)]Visual Studio, use the **Deploy** command to deploy the assemblies containing the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution and the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service to a local instance of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. This creates a BizTalk application that is populated with the assemblies.  
  
- From within Visual Studio, use the **BizTalk WCF Service Consuming Wizard** to generate the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] schemas and types necessary to consume the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service. An empty orchestration is generated as well that you can use and bind to a logical port. This orchestration is complied and deployed along with schemas and types. But the orchestration workflow processing is empty here and not used in this sample as this is merely a pure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] messaging scenario.  
  
- From the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, configure content-based routing by using the WCF-BasicHttp send port. You will configure the **SOAPAction** header that the target [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service expects to receive.  
  
- From the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, configure the filter expression to route any SOAP fault messages that a [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service can send to an output folder.  
  
- From within Internet Information Services (IIS) Manager, configure the Web application hosting the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service to expose its metadata. After it is enabled, the **BizTalk WCF Service Consuming Wizard** can obtain this metadata to generate types and schemas to access the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service.  
  
## Prerequisites  
 To perform the steps in this sample ensure that your environment installs the following prerequisites:  
  
- Both the computer that builds the assemblies and runs the deployment process, and the computer that runs the sample, require Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], Microsoft [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)], and Microsoft BizTalk Server.  
  
- The computer used to build the assemblies and run the deployment process requires Microsoft Visual Studio.  
  
- The computer that runs the sample requires the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] Adapters and the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] Administration Tools. These are options to install during setup of Microsoft BizTalk Server.  
  
- On the computers that you use to perform administrative tasks, you must run as a user account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group to configure the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application settings within the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console. This user account must also be a member of the local Administrators group for application deployment, managing host instances, and other tasks that may be required.  
  
- On any computer that requires [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] capability, complete the one-time setup procedure for the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] samples at [http://go.microsoft.com/fwlink/?LinkId=135510](http://go.microsoft.com/fwlink/?LinkId=135510).  
  
- On the computer that runs the sample and imports a binding or an .msi file into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ensure the host is not a trusted host or the import will fail.  
  
- You must download the walkthrough code and extract it to your computer.  This walkthrough is a part of the entire [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] Adapter Walkthrough package. You can download the file **WCFAdapterWalkthroughs.exe** from the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Developer Center at[http://go.microsoft.com/fwlink/?LinkId=194140](http://go.microsoft.com/fwlink/?LinkId=194140).  
  
## Deploy the sample WCF service  
  
1. Run the self-extracting **WCFBasicHttpSendAdapter.exe** file and extract the files into the **C:\WCFBasicHttpSendAdapter** folder.  
  
2. Open the **C:\WCFBasicHttpSendAdapter\WCFBasicHttpSendAdapter.sln** in Visual Studio.  
  
3. In Solution Explorer, expand the **BasicHttpWCFServiceConsuming** project. This project is the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service that will be called by the send port. It will be hosted in a managed host environment using Internet Information Services (IIS). Hosting in IIS uses message-based activation to manage the activation and lifetime of the service. Expand **App_Code**, and then open **OrderProcess.cs** to review. This [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service receives order request messages through the **OrderRequest** method. The OrderProcess.cs file contains the interface defition and implementation of the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service. It simply returns order response messages through the **OrderResponse** method.  
  
4. Review the OrderProcess.svc file. It contains only one line which is used to tell IIS to activate the service for a client application. The <strong>@ServiceHost</strong> attribute used to host the service is a point of extensibility within the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] programming model. A factory pattern uses **ServiceHostFactory** to create an instance of **ServiceHost** with an instance of the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service to handle incoming requests. Instantiation of this instance is based upon the **ServiceBehaviorAttribute.ConcurrencyMode** property, which determines whether a service supports one thread, multiple threads, or reentrant calls. Instantiation is also determined by the **ServiceBehavior.InstanceMode** property, which determines if a only one instance will serve all callers (singleton), if one instance will be created per call (stateless), or if one instance will be created for each session (stateful).  
  
   ```  
   <%@ServiceHost language=c# Debug="true" Service="Microsoft.Samples.BizTalk.WCF.BasicHttpSendAdapter.BasicHttpWcfServiceConsuming.OrderProcessServiceType" %>  
   ```  
  
5. In Visual Studio, in Solution Explorer, open **Web.config** to review. When hosted in IIS, a [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service is configured using a Web.config file instead of an app.config file as when hosted in a console application.  
  
   -   Make sure that the **httpGetEnabled** attribute of the \<**serviceMetaData**\> element is set to `true` so that the **BizTalk WCF Service Consuming Wizard** can consume the metadata for the service.  
  
   -   Make sure that the **mode** attribute of the \<**security**\> element is set to **None**. Because this walkthrough uses the **None** security mode, the Web application hosting this service must be configured to allow anonymous access.  
  
6. Because the **Microsoft.Samples.BizTalk.WCF.BasicHttpSendAdapter.BasicHttpWcfServiceConsuming** assembly must be installed in the GAC, it will need a strong name key file to complete the deployment process. Right-click the **BasicHttpWcfServiceConsuming** project, and then click **Properties**. On the **Properties** page, click **Signing**, and select **Sign the assembly**. Click the down arrow in the **Choose a strong name key file** drop-down list, click **\<New\>**, and enter `keyfile.snk` in the **key file name** textbox.  Uncheck **Protect my key file with a password**, and then click **OK**.  
  
7. In Solution Explorer, right-click **BasicHttpWcfServiceConsuming**, and then click **Rebuild**.  
  
8. Using Windows Explorer, copy the contents of **C:\WCFBasicHttpSendAdapter\BasicHttpWCFServiceConsuming** to the **C:\InetPub\wwwroot** folder.  
  
9. Configure the Web application to host the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service as follows:  
  
   1. Click **Start**, point to **Administrator Tools**, and then click **Internet Information Services (IIS) Manager**.  
  
   2. Create an application pool within which this service will run. Right-click **Application Pools**, click **Add Application Pool…**, enter a name for the application pool, and then click **OK**.  
  
   3. Expand **Application Pools**, right-click the application pool you just created, and then select **Advanced Settings**. Under **Process Model** section, enter the account which has access to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases under the **Identity** field.  
  
   4. Expand **Sites**, expand **Default Web Site**, right-click **BasicHttpWCFServiceConsuming**, and then click **Convert to Application** to create a Web application for this [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service.  
  
   5. In the **Convert to Application** dialog box, click **Select** to select the application pool created earlier, and then click **OK**.  
  
   6. In Features View, click the **Authentication** icon and ensure that the **Anonymous Authentication** option is **enabled**. This supports [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] services with the **None** security mode.  
  
10. Test the published [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service as follows:  
  
    1. In IIS Manager, expand **Web Sites**, and then expand **BasicHttpWCFServiceConsuming**.  
  
    2. In IIS Manager, in the right pane, right-click **OrderProcess.svc**, and then click **Browse**. This opens Internet Explorer to display the **OrderProcessServiceType Service** page that indicates you have successfully created a running [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service. The page also includes a full WSDL address that you can copy and use with the Service Metadata Tool (svcutil.exe) to create proxy code and a configuration file that can be used to develop a client application for the service.  
  
    3. Copy the full WSDL address to the system Clipboard. Do not copy the **“svcutil.exe”** part: **http://localhost/BasicHttpWcfServiceConsuming/OrderProcess.svc?wsdl**  
  
## Add the schemas and types for the WCF-BasicHttp adapter to the sample BizTalk application  
  
1. Since the adapter will call the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service it needs information from schemas and types about how to make that call to that service using the metadata. **BizTalkApp** provides the artifacts to consume the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service. In Visual Studio, in Solution Explorer, right-click **BizTalkApp**, click **Add**, and then click **Add Generated Items**.  
  
2. In the **Add Generated Items** dialog box, in the **Templates** section, select **Consume WCF Service**, and then click **Add**.  
  
3. On the **Welcome to the BizTalk WCF Service Consuming Wizard** page, click **Next**. This wizard will read the metadata and create schemas and types.  
  
4. On the **Metadata source** page, select the **Metadata Exchange (MEX) endpoint** option to consume metadata from the URL that you copied to the Clipboard in the previous procedure, and then click **Next**.  
  
5. On the **Metadata Endpoint** page, paste the full WSDL address that you copied in the previous procedure to the **Metadata Address** drop-down list, and then click **Get** to get the metadata document for the sample [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service. Obtaining the metadata enables the **Next** button. Click **Next** to continue.  
  
6. On the **Import WCF Service Metadata Summary** page, review your settings. This dialog box shows the namespace, XSD, and WSDL summaries of the metadata to be imported. It also shows where orchestration (.odx), bindings (.xml), and schema (.xsd) files will be written during the import process. Click **Import** to create the BizTalk artifacts and types to be used for consuming the sample [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service.  
  
7. On the **Completing the BizTalk WCF Service Consuming Wizard** page, click **Finish**.  
  
8. In Visual Studio, in Solution Explorer, the **BizTalk WCF Service Consuming Wizard** generates the following files:  
  
   - An orchestration file **OrderProcessServiceType.odx**. There are no workflow stages in this orchestration. However, you could add to it and bind it to logical ports to consume the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service. It does contain the important BizTalk types such as port types and multipart message types, which are used in this sample. To view this information, double-click the **OrderProcessServiceType.odx** orchestration. Click **View**, click **Other Windows**, and click **Orchestration View**. Expand **Types**, expand **Port Types**, and then expand **IOrderProcess**. You will see the **Submit** method. Expand that method and you will see the **OrderRequest** and **OrderResponse** port types. Click each port type and view their **Description** fields in the property browser and see the different WSDL input and output messages. Click **Multi-Part Message Types** and view the **OrderRequest** and **OrderResponse** multi-part message types. Click their **Description** fields and view the WDSL message names for each message type.  
  
   - Two schema files are generated. The first schema file (**OrderProcessServiceType_biztalk_WCF_basichttpsendadapter_basichttpWCFserviceconsuming.xsd**) defines the message types that the sample [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service uses. It uses the **OrderID** field in both **OrderRequest** and **OrderResponse** calls.  
  
   - The second schema file (**OrderProcessServiceType_schemas_microsoft_com_2003_10_Serialization.xsd**) is exported by [DataContractSerializer](http://go.microsoft.com/fwlink/?LinkId=81722) for the types, elements, and attributes from the namespace, http://schemas.microsoft.com/2003/10/Serialization/.  
  
   - Two binding files are generated, which will be used later to create the BizTalk application: **OrderProcessServiceType.BindingInfo.xml** and **OrderProcessServiceType_Custom.BindingInfo.xml**. In the general case you will typically use the non-custom binding file. But in some rare situations where you have a custom binding element use the custom binding file. The custom binding element creates send ports for the applications. Double-click the **OrderProcessServiceType.BindingInfo.xml** file and search for the **SendPort** definition line, and review the send port that will be created when you import this binding file into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]:  
  
     ```  
     <SendPort Name="WCFSendPort_OrderProcessServiceType_ServiceEndpoint" …  >  
     ```  
  
   - These files are used for the send port using the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] adapter to consume the sample [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service described in the metadata.  
  
## Deploy the sample BizTalk solution, BizTalkApp  
  
1. Deploy the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application as follows:  
  
   1. In Visual Studio, in Solution Explorer, right-click **BizTalkApp**, and then click **Properties** .  
  
   2. In the **Project Designer** window, click **Deployment** tab, and then change the **Server** property if you use a different database server for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Management database. Ensure the application name is **WCFBasicHttpSendAdapter**.  
  
   3. In Visual Studio, in Solution Explorer, right-click **BizTalkApp**, and then click **Rebuild**.  
  
   4. In Visual Studio, in Solution Explorer, right-click **BizTalkApp**, and then click **Deploy**.  This deploys the Microsoft.Samples.BizTalk.WCF.BasicHttpSendAdapter.BizTalkApp assembly to the GAC, and the artifacts to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application named **WCFBasicHttpSendAdapter**.  
  
2. Configure a WCF-BasicHttp send port in the BizTalk application as follows:  
  
   1. Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
   2. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Group**, expand **Applications**, right-click **WCFBasicHttpSendAdapter**, point to **Import**, and then click **Bindings**.  
  
   3. In the **Import Bindings** dialog box, go to the **C:\WCFBasicHttpSendAdapter\BizTalkApp** folder, select **OrderProcessServiceType.BindingInfo.xml**, and then click **Open**. This is one of the binding files created by the **BizTalk WCF Service Consuming Wizard** previously. This creates the **WCFSendPort_OrderProcessServiceType_ServiceEndpoint** send port.  
  
   4. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **WCFBasicHttpSendAdapter**, and then click **Send Ports**.  
  
   5. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, in the right pane, double-click **WCFSendPort_OrderProcessServiceType_ServiceEndpoint**, which was created by importing the binding file OrderProcessServiceType.BindingInfo.xml. This brings up the **Send Port Properties** dialog box.  
  
   6. In the **Send Port Properties** dialog box, click **Configure**.  
  
   7. On the **General** tab review the **Address(URI)** field of **<http://localhost/BasicHttpWcfServiceConsuming/OrderProcess.svc>**. This is the address of the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service hosted in IIS that the WCF-BasicHttp adapter will call.  
  
   8. Review the contents of the **SOAP Action header/Action** text box:  
  
      ```  
      <BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
        <Operation Name="Submit" Action="http://Microsoft.Samples.BizTalk.WCF.BasicHttpSendAdapter.BasicHttpWcfServiceConsuming/IOrderProcess/Submit" />  
      </BtsActionMapping>  
      ```  
  
       This field indicates the intent of the outgoing SOAP HTTP request message. Here it is to call the Submit operation on the IOrderProcess interface from the Microsoft.Samples.BizTalk.WCF.BasicHttpSendAdapter.BasicHttpWcfServiceConsuming namespace.  
  
      > [!NOTE]
      >  The binding file that the **BizTalk WCF Service Consuming Wizard** generates uses the action mapping format for the **StaticAction** property. When using content-based routing for the WCF send adapters to send messages to WCF services, you need to set the **BTS.Operation** property in pipeline components for the action mapping format as the field to be used for content-based routing. Alternatively, you can use the single action format for content-based routing. In this walkthrough, you use the single action format. For more information about the single action format and the action mapping format, see the **WCF-BasicHttp Transport Properties Dialog Box, Send, General** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
   9. Click **OK** twice to return to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
3. Create a one-way static receive port and a FILE receive location. A receive port is a logical container for one or more receive locations. This is where you will drop a sample [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] message that will be picked up by the File adapter, and then sent to the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service.  
  
   1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **WCFBasicHttpSendAdapter**, right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.  
  
   2. In the **Receive Port Properties** dialog box, in the **Name** text box, type `WCFBasicSendAdapter.ReceivePurchaseOrder`, and then click **OK**.  
  
   3. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, right-click **WCFBasicHttpSendAdapter.ReceivePurchaseOrder**, point to **New**, and then click **Receive Location**.  
  
   4. In the **Receive Location Properties** dialog box, in the **Name** text box, type `WCFBasicSendAdapter.ReceivePurchaseOrder.FILE`.  
  
   5. In the **Receive Location Properties** dialog box, in the **Transport** section next to **Type**, select **FILE** from the drop-down list, and then click **Configure**.  
  
   6. In the **FILE Transport Properties** dialog box, on the **General**  tab, in the **Receive folder** text box, type `C:\WCFBasicHttpSendAdapter\OrderRequestIn`, and then click **OK**.  
  
   7. In the **Receive Location Properties** dialog box, click **OK**.  
  
4. Create a filter to route messages to the WCF-BasicHttp send port from the FILE receive location that you created in the previous step. A filter associated with a port acts like a SQL “where” clause in that if it evaluates to true the message will be given to that port.  
  
   1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **WCFBasicHttpSendAdapter**, click **Send Ports**, and then double-click **WCFSendPort_OrderProcessServiceType_ServiceEndpoint**.  
  
   2. In the **Send Port Properties** dialog box, on the **Filters** tab, select **BTS.ReceivePortName** in the **Property** field, type `WCFBasicSendAdapter.ReceivePurchaseOrder` in the **Value** field, and then click **OK**. This filter expression routes incoming messages from the WCFBasicSendAdapter.ReceivePurchaseOrder receive port to this WCF-BasicHttp send port.  
  
5. Create two FILE send ports for the sample application. The first send port sends output response messages to the FILE port from the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service. The second send port is used to handle fault messages sent from the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service destined for the client.  
  
   1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **WCFBasicHttpSendAdapter**, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.  
  
   2. In the **Send Port Properties** dialog box, in the **Name** text box, type `WCFBasicSendAdapter.SendPurchaseOrder.FILE`.  
  
   3. In the **Send Port Properties** dialog box, in the **Transport** section next to Type, select **FILE** from the drop-down list, and then click **Configure**.  
  
   4. In the **FILE Transport Properties** dialog box, on the **General** tab, in the **Destination folder** text box, type `C:\WCFBasicHttpSendAdapter\OrderResponseOut`, and then click **OK**.  
  
   5. In the **Send Port Properties** dialog box, on the **Filters** tab, select **BTS.MessageType** in the **Property** field, type `http://Microsoft.Samples.BizTalk.WCF.BasicHttpSendAdapter.BasicHttpWCFServiceConsuming#OrderResponse` in the **Value** field to specify the response message type from the sample [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service, and then click **OK**. This filter expression routes response messages from the sample [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service to this FILE send port. The send port subscribes to messages of the OrderResponse type by specifying that type in the filter property. This is the message type of the response message from the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service.  
  
   6. In the **Send Port Properties** dialog box, click **OK**.  
  
   7. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **WCFBasicHttpSendAdapter**, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.  
  
   8. In the **Send Port Properties** dialog box, in the **Name** text box, type `WCFAdapterErrorSend.FILE`.  
  
   9. In the **Send Port Properties** dialog box, in the **Transport** section next to **Type**, select **FILE** from the drop-down list, and then click **Configure**.  
  
   10. In the **FILE Transport Properties** dialog box, on the **General** tab, in the **Destination folder** text box, type `C:\WCFBasicHttpSendAdapter\WCFAdapterErrorOut\`, and then click **OK**.  
  
   11. In the **Send Port Properties** dialog box, on the **Filters** tab, select **WCF.IsFault** in the **Property** field, type `True` in the **Value** field, and then click **OK**. Within an application an exception or fault can be detected by checking the **WCF.IsFault** property of the message sent back to the caller. This property will be set to **True** if the message being sent is a SOAP fault message. This filter expression routes fault messages from the sample [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service to this FILE send port.  
  
6. Specify the host name and bindings for the sample application as follows:  
  
    In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **WCFBasicHttpSendAdapter**, expand **Orchestrations**, right-click the **Microsoft.Samples.BizTalk.WCF.BasicHttpSendAdapter.BizTalkApp.OrderProcessServiceTypeClient** orchestration, click **Properties**, click **Bindings**, set **Host** to **BizTalkServerApplication**, and then click **OK** to save the configuration.  
  
## Test the sample solution with the WCF-BasicHttp send adapter  
  
1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, right-click **WCFBasicHttpSendAdapter**, and then click **Start**.  
  
2. In the **Start** dialog box, click **Start**.  
  
3. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **Platform Settings**, expand **Host Instances**, right-click **BizTalkServerApplication** or another appropriate host instance, and then click **Restart**.  
  
4. Open a command prompt, type **iisreset** to recycle IIS and its dependent services, and then press ENTER.  
  
5. At the command prompt, copy **C:\WCFBasicHttpSendAdapter\TestData\WCFBasicSendAdapter.OrderRequest.Sample.xml** to the **C:\WCFBasicHttpSendAdapter\OrderRequestIn** folder. This message is routed to the two-way **WcfSendPort_OrderProcessServiceType_ServiceEndpoint** static Solicit-Response send port.  The send side of this two-way send port calls **Submit** method on the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service hosted in IIS. The result is returned to the response port of the **WcfSendPort_OrderProcessServiceType_ServiceEndpoint** send port.  The **WCFBasicSendAdapter.SendPurchaseOrder.FILE** send port has a subscription that will be triggered when the type of the message is **<http://Microsoft.Samples.BizTalk.WCF.BasicHttpSendAdapter.BasicHttpWCFServiceConsuming#OrderResponse>**.It will get the successfully processed message and write it out to the **C:\WCFBasicHttpSendAdapter\OrderResponseOut** folder.  
  
6. Check the **C:\WCFBasicHttpSendAdapter\OrderResponseOut** folder for a response message from the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service.  
  
7. At the command prompt, **C:\WCFBasicHttpSendAdapter\TestData\WCFBasicSendAdapter.OrderRequest.Invalid.xml** to the **C:\WCFBasicHttpSendAdapter\OrderRequestIn** folder. This message contains an invalid namespace so that the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service returns a fault message.  
  
8. Check the **C:\WCFBasicHttpSendAdapter\WCFAdapterErrorOut** folder for an XML file containing the fault message from the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service. Look at the \<**faultstring**\> field showing the cause of the fault message to be an invalid message body.  
  
## See Also  
 [Walkthrough: Publishing WCF Services with the WCF-BasicHttp Adapter](../core/walkthrough-publishing-wcf-services-with-the-wcf-basichttp-adapter.md)   
 [How to Use the BizTalk WCF Service Consuming Wizard to Consume a WCF Service](../core/how-to-use-the-biztalk-wcf-service-consuming-wizard-to-consume-a-wcf-service.md)   
 [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md)