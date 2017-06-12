---
title: "BizTalk Web Services Publishing Wizard | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.webservices"
ms.assetid: 44e7419f-a39f-4d15-867a-60bcedf4d2fb
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BizTalk Web Services Publishing Wizard
Use the **BizTalk Web Services Publishing Wizard** to create and publish BizTalk orchestrations as Web services, and to publish schemas as Web services. For general usage information about the BizTalk Web Services Publishing Wizard, see [Using Web Services](../core/using-web-services.md).  
  
## Create Web Services page  
 Use this page to select a method of creating your Web service.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Publish BizTalk orchestrations as web services**|Publish a Web service based on selected orchestrations and Web ports in a BizTalk assembly.|  
|**Publish schemas as web services**|Define Web methods and messages of a Web service using selected schemas from BizTalk assemblies as request and/or response message parts.|  
  
## BizTalk Assembly page  
 Use this page to select a BizTalk assembly to publish a Web service from.  
  
|Use this|To do this|  
|--------------|----------------|  
|**BizTalk assembly file (\*.dll)**|Select a BizTalk assembly.|  
  
 Your assembly does not need to be deployed to publish a Web service.  
  
 If your assembly has dependencies, you must resolve any dependencies in your assembly before you can publish a Web service from it. The assembly must be deployed and properly bound to be used at runtime.  
  
## Orchestrations and Ports page  
 You can select the orchestrations and ports in the assembly to expose in your published Web service. Only public ports are visible.  
  
 Select the orchestrations and ports that you want to export.  
  
## Web Service Properties page  
 Use this page to specify the properties for the Web service.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Target namespace of web service**|Select a target namespace of a Web service. The target namespace appears in the Web Service Description Language (WSDL) file. The **System.Uri** constructor is used to determine the validity.|  
|**Add additional SOAP headers**|Add schemas from BizTalk assemblies to use as request and response SOAP headers.|  
|**Support unknown SOAP headers**|Add support for unknown headers.|  
|**Add SharePoint Portal Server 2003 Single Sign-On support**|Add support for Single Sign-On (SSO) in SharePoint Portal Server 2003.|  
  
 You can click the **Advanced** button to control advanced properties that control message format and message processing behavior.  
  
## Web Service Advanced Properties Page  
 Use this page to customize global web service and web method attributes.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Soap Parameter Style**|Specify how parameters are formatted in a SOAP message. Options include:<br /><br /> -   **Bare**: Parameters sent to and from an XML Web service method are placed in the XML elements directly following the **Body** element of a SOAP request or SOAP response.<br />-   **Wrapped (Default)**: Parameters sent to and from an XML Web service method are encapsulated within a single XML element following the **Body** element of the XML portion of a SOAP request or SOAP response.|  
|**Conformance Claims**|Specify the web services interoperability (WSI) business process 1.1 (BP1.1) conformance claims made by the web service. **Note:**  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cannot consume web services using BP1.1 conformance claims. If you will be consuming the service from BTS2004, do not use conformance claims.|  
|**Force Request Response**|Specify that one-way BizTalk operations should be exposed as request-response web methods.|  
  
## Web Service Project page  
 Use this page to customize your published Web service.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Project name**|Enter a project name.|  
|**Project location**|Specify the path name of the virtual directory where the Web service is published. **Important:**  You must use ANSI characters.|  
|**Overwrite existing project**|Overwrite the existing project when you republish a Web service.|  
|**Browse button**|Search disk locations for a file location.|  
|**Allow anonymous access to web service**|Sets the **AuthAnonymous** flag on the published virtual directory. This flag is useful in a development environment.|  
|**Create BizTalk Receive locations**|Generates a BindingInfo.xml binding file to create the receive locations that correspond to the published Web service.<br /><br /> The BindingInfo.xml file can be imported by the development command-line tool or wizard to create the necessary receive locations. You can find BindingInfo.xml in the temp folder of the published Web service's virtual directory.|  
  
## Request SOAP Headers/Response SOAP Headers page  
 Use this page to add and remove schemas from BizTalk assemblies to use as request and response SOAP headers.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Add** button|Add a schema by specifying the path name to a BizTalk assembly that contains document schemas.|  
|**Remove** button|Remove a schema.|  
  
> [!NOTE]
>  Top-level elements of ComplexType elements are listed and can be used as SOAP headers.  
  
 Use these pages to select one or more schema types from BizTalk assemblies to use as request and response SOAP headers.  
  
|Use this|To do this|  
|--------------|----------------|  
|**BizTalk assembly file (\*.dll)**|Select a BizTalk assembly.|  
|**Browse** button|Search disk locations for a file location.|  
  
## Web Service page  
 Use this page to describe the Web service that you are creating.  
  
 Right-click a node to view properties and menu options to add, rename, or delete a Web service or Web method.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Add web service**|Add a Web service.|  
|**Rename web service description**|Rename a Web service. Type a new name for your Web service.|  
|**Add web method**|Add a one-way Web method.<br /><br /> Add a request-response Web method.|  
|**Select schema type**|Select a schema type in **Request Message Type/Request Message Type** page.|  
|**Rename web message part**|Rename the Web message part.|  
  
## Request Message Type/Response Message Type page  
 Use these pages to select one or more schema types from BizTalk assemblies to use as request and response SOAP headers.  
  
|Use this|To do this|  
|--------------|----------------|  
|**BizTalk assembly file (\*.dll)**|Select a BizTalk assembly.|  
|**Browse** button|Search disk locations for a file location.|  
  
## Web Service Project Summary page  
 Use this page to review your settings. Click **Back** to make any changes to your published Web service. Click **Create** to create your published Web service.  
  
## Completing the Web Services Publishing Wizard page  
 Use this page to determine if you have successfully published your Web service.  
  
|Use this|To do this|  
|--------------|----------------|  
|**link to published Web service**|Go to your published Web service project.|  
  
## See Also  
 [How to Use the BizTalk Web Services Publishing Wizard to Publish an Orchestration as a Web Service](../core/publish-orchestration-as-web-service--biztalk-web-services-publishing-wizard.md)   
 [How to Use the BizTalk Web Services Publishing Wizard to Publish Schemas as a Web Service](../core/publish-schemas-as-web-services-with-biztalk-web-services-publishing-wizard.md)   
 [Considerations When Publishing Web Services](../core/considerations-when-publishing-web-services.md)