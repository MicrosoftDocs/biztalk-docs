---
title: "Considerations When Publishing WCF Services with the WCF Receive Adapters | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "publishing, WCF services"
  - "WCF adapters, best practices"
  - "WCF adapters, receive adapters"
  - "WCF services, publishing"
  - "best practices, WCF adapters"
ms.assetid: 797b7ffd-534c-4f09-9738-fb17b208bc96
caps.latest.revision: 34
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Considerations When Publishing WCF Services with the WCF Receive Adapters
This topic provides information that you should take into consideration when publishing WCF services with the WCF receive adapters.  Publishing a service using a WCF adapter allows it to be called by a WCF client as if it were a typical WCF service.  
  
## In-Process Hosting  
 Hosting the receive location within the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] process space, btsntsvc.exe, allows the benefits of simplified development and deployment. Additionally, it creates more host instances than hosting in IIS to take advantage of the high-availability and load balancing capabilities of  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  For information in hosting outside of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] process in IIS refer to [Configuring IIS for the Isolated WCF Receive Adapters](../core/configuring-iis-for-the-isolated-wcf-receive-adapters.md).  
  
## Set the IsOneWay property of WCF services published with the WCF adapters (except for the WCF-NetMsmq receive adapter) to false  
 The **System.ServiceModel.OperationContractAttribute.IsOneWay** property of WCF services published with the WCF adapters—except for services published with the WCF-NetMsmq receive adapter where it is set to **true** —is set to **false** even for the one-way receive locations. If the **IsOneWay** property is set to **false**, even methods that return a **void** result in a reply message. In this case, the infrastructure creates and sends an empty message to indicate to the caller that the method has returned. Using this approach enables the infrastructure to send exceptions thrown by the service operation back to the client.  
  
 To consume WCF services published with the WCF adapters (except for the WCF-NetMsmq receive adapter) in which **IsOneWay** is **false**, the **IsOneWay** property on the client side must be set to **false** as follows:  
  
```  
[ServiceContract(Namespace="Microsoft.WCF.Documentation")]  
  public interface ISampleService{  
    [OperationContract(IsOneWay=false, ReplyAction="*",Action="…"]  
    string SampleMethod(string msg);  
}  
```  
  
> [!NOTE]
>  Because the default value of the **IsOneWay** property is **false**, you do not have to specify the property in the code.  
  
## The ReplyAction property of the OperationContractAttribute on the client side should be set to "*" (an asterisk) when consuming WCF services published with one-way receive locations  
 The **System.ServiceModel.OperationContractAttribute.ReplyAction** property of the **System.ServiceModel.OperationContractAttribute** can be used on the client side to specify the value of the SOAP action for the response messages from WCF services.  
  
 In addition to specifying a particular value for the action header of the reply message (to notify the client this is a reply and what action to be taken), you can also specify the string "*" (an asterisk). Specifying an asterisk in a client application instructs the client not to validate the reply action in response messages that the service sends.  
  
 To consume a WCF service published by a one-way receive location, the proxy method for the WCF service must return **void**, in which case the proxy method expects that the WCF service will send an empty message to indicate to the caller that the method has returned. For the proxy method to receive this empty message, the **ReplyAction** property of the **OperationContractAttribute** should be set to "*" (an asterisk) as follows:  
  
```  
[ServiceContract(Namespace="Microsoft.WCF.Documentation")]  
  public interface ISampleService{  
    [OperationContract(IsOneWay=false, ReplyAction="*",Action="…"]  
    string SampleMethod(string msg);  
}  
```  
  
> [!NOTE]
>  You do not have to set the **ReplyAction** property to "\*" (an asterisk) for the WCF-NetMsmq adapter, because the WCF-NetMsmq adapter requires the WCF clients to set the **IsOneWay** property to **true**.  
  
## An isolated host instance can run only one adapter  
 An isolated host instance can run only one adapter. If you configure the receive handlers of multiple isolated adapters such as HTTP, SOAP, and WCF adapters with one isolated host, you must create multiple application pools, one application pool for each adapter. For more information about BizTalk isolated hosts, see [Enabling Web Services](../core/enabling-web-services.md).  
  
## Use the "Template -- content specified by template" option when sending non-XML content as response messages  
 The WCF adapters with **Body -- BizTalk response message body** (the default value) option do not allow sending non-XML messages such as character data and bitmap images. You can use the **Template -- content specified by template** option for the WCF adapters to send non-XML messages. For more information about how to use the template, see [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md).  
  
## Setting up the permissions for a WCF service published with the WCF Service Publishing Wizard  
 When using ASP.NET applications created with the WCF Service Publishing Wizard on the [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] or [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] platform, errors relating to accessing DLLs during WCF service invocation may occur. These errors are typically related to issues with default [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] and [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] security. For more information about these errors, see the Microsoft Help and Support article called "You Receive a "System.IO.FileNotFoundException" Error When the Client Application Calls a Web Service" on the Help and Support Web site at [http://go.microsoft.com/fwlink/?LinkId=43659](http://go.microsoft.com/fwlink/?LinkId=43659).  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] requires that the process running the WCF service is granted the appropriate permissions whether an in-process host or an isolated host runs the service. Under [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] and [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] the default Windows group for isolated hosts is the Isolated Host Users Group, so adding the permissions to the Isolated Host Users Group should resolve this issue.  
  
#### To add the permissions to the Isolated Host Users Group  
  
1.  In Microsoft Windows Explorer, locate the %windir%\temp directory.  
  
2.  Right-click %windir%\temp, and then click **Properties**.  
  
3.  In the **Properties** dialog box, click the **Security** tab.  
  
4.  Click **Add**, select **the Isolated Host Users Group**, and then click **OK**.  
  
## Setting up the permissions for a WCF receive location with the WCF-NetMsmq adapter  
 When a WCF client using the NetMsmqBinding sends a message to a WCF service published with the WCF-NetMsmq adapter, it addresses the message to the target queue, which is the queue managed by the service's queue manager. The queue manager on the client sends the message to a transmission (or outgoing) queue. The transmission queue is a queue on the client-side queue manager that stores messages for transmission to the target queue.  
  
 The service's queue manager accepts messages addressed to the target queues it owns and stores the messages. Then, the service makes requests to read from the target queue, and the queue manager delivers the messages to the service. For this reason, the service account for the BizTalk host instance hosting the receive location should have the permissions to read from the target queue.  
  
## Use an empty body path expression to receive a SOAP message with character data in the content of the SOAP Body element  
 For a WCF receive adapter to create a BizTalk message from an incoming response message with character data in the content of the SOAP **Body** element, as shown in the following example, you should leave the **Body path expression** text box empty on the **Message** tab in the WCF adapter transport properties dialog box.  
  
```  
<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://www.w3.org/2005/08/addressing">  
    <s:Header>  
      ...  
    </s:Header>  
    <s:Body>Contoso</s:Body>  
</s:Envelope>  
```  
  
 If you select the **Envelope** or **Body** option, the adapter cannot create the BizTalk message from the previous incoming message. The message is not suspended because messages that fail in the inbound SOAP marshaling processing are not suspended. For more information about how to use the body path expression on the **Message** tab, see [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md).  
  
> [!NOTE]
>  You can use the TraceViewer tool (SvcTraceViewer.exe) in the Windows SDK by configuring the BTSNTSvc.exe.config.file. For more information about the Windows SDK, see "What's New in the Windows SDK" at [http://go.microsoft.com/fwlink/?LinkId=75219](http://go.microsoft.com/fwlink/?LinkId=75219). For more information about the TraceViewer tool, see "TraceViewer Tool (SvcTraceViewer.exe)" at [http://go.microsoft.com/fwlink/?LinkId=75218](http://go.microsoft.com/fwlink/?LinkId=75218).  
  
## Using schemas that reference other schemas  
 You can use the **redefine**, **include**, and **import** elements when your schemas become large and complex, or when the schemas that represent your different types of instance messages have some portions in common. It can be useful to combine smaller schemas into the schemas that ultimately define the structure of the instance messages you plan to exchange with trading partners. You can publish these schemas as WCF services by using the BizTalk WCF Service Publishing Wizard.  
  
 You should use the BizTalk WCF Service Consuming Wizard to create the BizTalk artifacts necessary to consume the WCF services from a BizTalk project. If you want to consume the WCF services from a .NET application, you should use the Service Model Metadata Utility tool (Svcutil.exe) to create the proxy class for the WCF services. For more information about how to use schemas that reference other schemas, see [Schemas That Use Other Schemas](../core/schemas-that-use-other-schemas.md) and [How to Create Schemas That Use Other Schemas](../core/how-to-create-schemas-that-use-other-schemas.md). For more information about Svcutil.exe, see "Service Model Metadata Utility Tool (Svcutil.exe)" at [http://go.microsoft.com/fwlink/?LinkID=74696](http://go.microsoft.com/fwlink/?LinkID=74696).  
  
 The following table shows the limitations and considerations that you need to know when consuming published WCF services with schemas that use other schemas.  
  
|XML schema element|Consuming WCF services published with the BizTalk WCF Service Publishing Wizard|Consuming WCF services hosted by .NET applications|  
|------------------------|-------------------------------------------------------------------------------------|--------------------------------------------------------|  
|\<import\>|Supported with both the BizTalk WCF Service Consuming Wizard and Svcutil.exe|Supported with both the BizTalk WCF Service Consuming Wizard and Svcutil.exe|  
|\<include\>|Supported with both the BizTalk WCF Service Consuming Wizard and Svcutil.exe **Note:**  Svcutil.exe may raise a warning message when creating the proxy class.|Supported with both the BizTalk WCF Service Consuming Wizard and Svcutil.exe **Note:**  Svcutil.exe may raise a warning message when creating the proxy class.|  
|\<redefine\>|-   Supported with the BizTalk WCF Service Consuming Wizard<br />-   Limited support by Svcutil.exe **Note:**  Svcutil.exe has the same limitation for the **redefine** element as XSD.exe has.|Supported with both the BizTalk WCF Service Consuming Wizard and Svcutil.exe **Note:**  Svcutil.exe may raise a warning message when creating the proxy class.|  
  
> [!NOTE]
>  Svcutil.exe may raise a warning message when creating the proxy class against the published BizTalk WCF service with the schemas using the **include** and **redefine** elements. For example, "The global element has already been declared."  
  
## Ensure that an in-process WCF receive location is not disabled after you change the computer name part in its service endpoint address  
 If you change the computer name part in the **Address (URI)** text box of a running in-process WCF receive location, we recommend that you use the BizTalk Administration console to check whether the receive location is still running. For example, if you change a service endpoint address using the WCF-NetTcp receive adapter, **net.tcp://\<**<em>Your Computer Name</em>**\>/samplepath**, to **net.tcp://localhost/samplepath**, the receive location may be disabled with a **Service.InvalidOperationException**. If you change only the computer name part in the service endpoint address without modifying the path part, make sure that the receive location is not disabled, and enable it if necessary.  
  
## Set the appropriate MSDTC Security Configuration options on client computers communicating with remote WCF receive locations through a transaction protocol  
 WCF-NetTcp, WCF-WSHttp, and WCF-NetNamedPipe receive adapters can participate in transactional coordination processes that WCF clients manage with the **WS-AtomicTransaction** and **OleTransaction** transaction protocols. Messages can be transmitted to the destination receive locations and deleted from the MessageBox database in a transactional context by using the transaction protocols.  
  
 To communicate with remote WCF receive locations by using the transaction protocols, you must appropriately configure MSDTC **Security Configuration** options on WCF client computers. The following table lists the required values for the options that are available in the MSDTC **Security Configuration** dialog box:  
  
|Configuration option|Default value|Recommended value|  
|--------------------------|-------------------|-----------------------|  
|Network DTC Access|Disabled|Enabled|  
|Allow Outbound|Disabled|Enabled|  
|Mutual Authentication Required|Enabled|Enabled if the corresponding remote receive locations are running Windows Server 2003 SP1 or SP2, and are configured with **Mutual Authentication Required**.|  
|Incoming Caller Authentication Required|Disabled|Enabled if running MSDTC on a cluster.|  
  
 After you apply these changes, you have to restart the MSDTC service.  
  
 To access the MSDTC **Security Configuration** dialog box, follow these steps:  
  
1.  Click **Start**, click **Run**, and type **dcomcnfg** to launch the **Component Services** Management console.  
  
2.  Expand **Component Services**, expand **Computers**, right-click **My Computer**, and then click **Properties**.  
  
3.  In the **My Computer Properties** dialog box, click the **MSDTC** tab, and then click **Security Configuration** to display the **Security Configuration** dialog box.  
  
## Explanation of the SOAP wrapper when using the BizTalk WCF Service Publishing Wizard  
 When an orchestration is exposed as a [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] service by using the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] Service Publishing Wizard, a wrapper is generated. This wrapper uses the method name of the port in the XML message to which the message is sent. This wrapper is the default for Microsoft SOAP envelopes. It allows [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] to wrap the multi-part SOAP message in one WCF message to be transmitted to the endpoint by the adapter.  
  
 As a best practice, either the sender should use a wrapper and the receiver should expect it, or the sender should not use a wrapper and the receiver should expect the raw [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] message. Failure to agree ahead of time on whether to use a wrapper can cause incompatibility issues between what is sent and what is received.