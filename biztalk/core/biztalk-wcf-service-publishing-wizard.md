---
title: "BizTalk WCF Service Publishing Wizard | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.wcf-service,publishing.wizard"
helpviewer_keywords: 
  - "bts09.wcf-service.publishing.wizard"
ms.assetid: d2cdd4d6-af92-447d-959a-6eff26c7db37
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BizTalk WCF Service Publishing Wizard
Use the BizTalk WCF Service Publishing Wizard to create and publish BizTalk orchestrations as WCF services, and to publish schemas as WCF services for the isolated WCF adapters hosted by Web applications running in IIS. You can also use the BizTalk WCF Service Publishing Wizard to publish service metadata for any WCF locations for the in-process WCF adapters. For general usage information about the BizTalk WCF Service Publishing Wizard, see [Using WCF Services](../core/using-wcf-services.md).  
  
> [!NOTE]
>  When running the BizTalk WCF Service Publishing Wizard on a Windows operating system that uses User Access Control (UAC), such a [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] and [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)], you may need to disable UAC to run the wizard to completion. This can be done through the MSCONFIG.EXE system utility.  
  
> [!NOTE]
>  You may need to register the .svc extension with Internet Information Server (IIS) before you are able to browse to the service using the **WCF Service Location Page**.  You can find information on this topic at either [Deploying an Internet Information Services-Hosted WCF Service](http://msdn.microsoft.com/en-us/library/aa751792.aspx) or [Deploying an IIS-Hosted WCF Service](http://msdn.microsoft.com/en-us/library/aa751792\(VS.85\).aspx).  
  
## WCF Service Type  
 Use this page to select the type of WCF service to publish.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Service endpoint**|Publish the WCF services based on selected BizTalk orchestrations or schemas in a BizTalk assembly.|  
|**Adapter name (Transport type)**|Specify the WCF adapter with which to publish these WCF services. Valid values only include the isolated WCF receive adapters as the following:<br /><br /> -   **WCF-BasicHttp**<br />-   **WCF-WSHttp**<br />-   **WCF-CustomIsolated**<br /><br /> You have to republish the WCF services if you want to change this adapter type.|  
|**Enable metadata endpoint**|Indicate whether the isolated WCF receive location hosted by Internet Information Services (IIS) publish service metadata for retrieval using an HTTP/GET request. By enabling this check-box, the wizard generates Web.config where the **httpGetEnabled** attribute of the **\<serviceMetadata>** element is set to **true**. You can use a metadata import tool (such as SvcUtil.exe) to generate the client code required to call this service in the development environment. To prevent unintentional disclosure of potentially sensitive service metadata, it is recommended to disable this behavior on the production environment.|  
|**Create BizTalk receive locations in the following application**|Specify whether to create the receive locations for the WCF services in the BizTalk application specified in the **BizTalk application name** property.|  
|**BizTalk application name**|Specify the BizTalk application where the receive locations for the WCF services are created.|  
|**Metadata only endpoint (MEX)**|Use this option for to publish service metadata of the existing WCF receive locations for retrieval using an HTTP/GET request. By using this option, you can publish service metadata of an in-process WCF receive adapter through IIS. By enabling this option, the wizard generates Web.config where the **httpGetEnabled** attribute of the **\<serviceMetadata>** element is set to **true**. You can use a metadata import tool (such as SvcUtil.exe) to generate the client code required to call this service in the development environment. To prevent unintentional disclosure of potentially sensitive service metadata, it is recommended to disable this behavior on the production environment. **Note:**  When you select the Metadata only endpoint (MEX), make sure not to leave the Publish metadata for receive location drop-down list blank.|  
|**Publish metadata for receive location**|Specify the WCF receive location for which to publish service metadata through IIS.|  
  
## Create WCF Service Page  
 Use this page to select a method of creating your WCF service.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Publish BizTalk orchestrations as WCF service**|Publish WCF services based on selected orchestrations and ports in a BizTalk assembly.|  
|**Publish schemas as WCF service**|Publish WCF services by specifying operations and messages of WCF services using selected schemas from BizTalk assemblies as request and/or response message parts.|  
  
## BizTalk Assembly Page  
 Use this page to select a BizTalk assembly to publish WCF services from.  
  
|Use this|To do this|  
|--------------|----------------|  
|**BizTalk assembly file (\*.dll)**|Select a BizTalk assembly.|  
  
 Your assembly does not need to be deployed to publish WCF services at design time.  
  
 If your assembly has dependencies, you must resolve any dependencies in your assembly before you can publish WCF services from it. The assembly must be deployed and properly bound to be used at run time.  
  
## Orchestrations and Ports Page  
 Use this page to select orchestrations and ports to publish in WCF services.  
  
|Use this|To do this|  
|--------------|----------------|  
|**BizTalk assembly description**|Select the orchestrations and ports that you want to export. You can select the orchestrations and ports in the assembly to expose in your published WCF services. Only public ports are visible.|  
|**Merge all selected ports into a single WCF service**|Specify whether to merge all the selected ports into a single WCF service. If this check box is cleared, one service can have only one port, which can result in multiple services being generated. **Note:**  If you select this check box, all operations in a single WCF service must have unique names in the service. <br /><br /> The default value is cleared.|  
  
## WCF Service Properties Page  
 Use this page to specify the properties for the WCF services.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Target namespace of WCF service**|Select a target namespace of the WCF services. The target namespace appears in the Web Services Description Language (WSDL) file. The **System.Uri** constructor is used to determine the validity of this namespace.|  
  
## WCF Service Location Page  
 Use this page to specify the location of the WCF services to create.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Location (http://host[:port]/path)**|Specify the path name of the virtual directory where the WCF services are published. **Important:**  You must use ANSI characters.|  
|**Overwrite existing location**|Overwrite the existing location when you republish the WCF services.|  
|**Browse button**|Search the virtual directory for the WCF services.|  
|**Allow anonymous access to WCF service**|Set the **AuthAnonymous**flag on the published virtual directory.|  
  
## WCF Service Page  
 Use this page to describe the WCF service that you are creating. Right-click a node to view properties and menu options to add, rename, or delete a WCF service or Web method.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Web service description**|Display the detail information about the WCF services published. When you click a node in this tree view, the **Information** text box displays more detail information about the node.<br /><br /> The default value is **BizTalkWcfService**.|  
|**Information**|Display more detail information about the node selected in the **Web service description** view.|  
|**Add web service**|Add a WCF service. To run this command, right-click the Web service description name, and then click **Add web service**.|  
|**Rename web service description**|Rename a Web service description. To run this command, right-click the Web service description name, and then click **Rename web service description**.|  
|**Add web method**|Add a Web method in the WCF service selected in the **Web service description** view. To run this command, right-click a WCF service, click **Add web method**, and then click the message exchange pattern for the Web method: **One-way** or **Request-response**.|  
|**Rename web service**|Rename the WCF service selected in the **Web service description** view. To run this command, right-click a WCF service, and then click **Rename web service**.|  
|**Delete web service**|Delete the WCF service selected in the **Web service description** view. To run this command, right-click a WCF service, and then click **Delete web service**.|  
|**Rename web method**|Rename the Web method selected in the **Web service description** view. To run this command, right-click a Web method, and then click **Rename web method**.|  
|**Delete web method**|Delete the Web method selected in the **Web service description** view. To run this command, right-click a Web method, and then click **Delete web method**.|  
|**Select schema type**|Select a schema type in the **Request Message Type** or **Response Message Type** dialog box. To run this command, right-click a WCF message, and then click **Select schema type**. This command opens the **Request Message Type** or **Response Message Type** dialog box depending on the direction of the selected WCF message: **Input** or **Output**.|  
|**Rename web message**|Rename the WCF message selected in the **Web service description** view. To run this command, right-click a WCF message, and then click **Rename web message**.|  
  
### Request Message Type/Response Message Type  
 Use these dialog boxes to select a message type from BizTalk assemblies to use as a request or response WCF message.  
  
|Use this|To do this|  
|--------------|----------------|  
|**BizTalk assembly file (\*.dll)**|Select a BizTalk assembly.|  
|**Browse**|Search disk locations for a file location.|  
|**Available schema types**|Display the message types included in the BizTalk assembly selected in the **BizTalk assembly file (\*.dll)** property. You can select a message type to use as a request or response WCF message.|  
  
## WCF Service Summary Page  
 Use this page to review your settings. Click **Back** to make any changes to your published WCF services. Click **Create** to create your published WCF services.  
  
## Completing the BizTalk WCF Service Publishing Wizard Page  
 Use this page to determine if you have successfully published your WCF service.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Run this wizard, click Finish**|Specify whether to run this wizard again.|  
  
## See Also  
 [Considerations When Publishing WCF Services with the WCF Receive Adapters](../core/considerations-when-publishing-wcf-services-with-the-wcf-receive-adapters.md)   
 [How to Use the BizTalk WCF Service Publishing Wizard to Publish Orchestrations as WCF Services](../core/publish-orchestrations-as-wcf-services--biztalk-wcf-service-publishing-wizard.md)   
 [How to Use the BizTalk WCF Service Publishing Wizard to Publish Schemas as WCF Services](../core/publish-schemas-as-wcf-services--use-the-biztalk-wcf-service-publishing-wizard.md)   
 [Walkthrough: Publishing WCF Services with the WCF-BasicHttp Adapter](../core/walkthrough-publishing-wcf-services-with-the-wcf-basichttp-adapter.md)   
 [Walkthrough: Publishing WCF Services with the WCF-NetMsmq Adapter](../core/walkthrough-publishing-wcf-services-with-the-wcf-netmsmq-adapter.md)