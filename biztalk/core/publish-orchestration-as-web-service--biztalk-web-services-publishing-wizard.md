---
title: "How to Use the BizTalk Web Services Publishing Wizard to Publish an Orchestration as a Web Service | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Web services, publishing"
  - "BizTalk Web Services Publishing Wizard, publishing"
  - "BizTalk Web Services Publishing Wizard"
  - "Web services, orchestrations"
  - "BizTalk Web Services Publishing Wizard, orchestrations"
  - "BizTalk Web Services Publishing Wizard, about BizTalk Web Services Publishing Wizard"
  - "orchestrations, publishing"
ms.assetid: d990f8e4-88ce-4718-8a94-63796b8d92dc
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Use the BizTalk Web Services Publishing Wizard to Publish an Orchestration as a Web Service
You use the BizTalk Web Services Publishing Wizard to publish an orchestration as a Web service.  
  
> [!NOTE]
>  You must build your BizTalk projects prior to running the BizTalk Web Services Publishing Wizard.  
  
> [!NOTE]
>  You can use a command line tool, BTSWebSvcPub.exe, to publish an orchestration as Web service. For more information, see [BTSWebSvcPub Command-Line Reference](../core/btswebsvcpub-command-line-reference.md).  
  
### To publish an orchestration as a Web service  
  
1.  Click **Start**, point to **All Programs**, point to **Microsoft BizTalk Server**, and then click **BizTalk Web Services Publishing Wizard**.  
  
2.  On the **Welcome to the BizTalk Web Services Publishing Wizard** page, click **Next**.  
  
3.  On the **Create Web Service** page, select **Publish BizTalk orchestrations as web services**, and then click **Next**.  
  
4.  On the **BizTalk Assembly** page, in the BizTalk assembly file (\*.dll) text box, type the name of the BizTalk assembly file or click **Browse** to browse to the assembly containing the orchestration(s) to publish, and then click **Next**.  
  
    > [!NOTE]
    >  Before choosing a BizTalk assembly file, copy all of the dependent assemblies into the same folder with the BizTalk assembly or install the dependent assemblies to the Global Assembly Cache (GAC).  
  
    > [!NOTE]
    >  If you installed the BizTalk assembly file into the GAC, make sure that the assembly in the GAC has been updated with the assembly that you will select in the **BizTalk Assembly** dialog box. If the GAC has the same fully qualified name, the BizTalk Web Services Publishing Wizard uses the assembly file in the GAC instead of the one you selected.  
  
    > [!NOTE]
    >  If you open the BizTalk Web Services Publishing Wizard in the Visual Studio containing an orchestration, the BizTalk assembly file populates with the assembly containing the orchestration.  
  
    > [!NOTE]
    >  Paths over 260 characters may get an error message that the path is too long.  
  
5.  On the **Orchestrations and Ports** page, expand the tree nodes for each assembly and orchestration by clicking the plus sign. Select orchestrations and ports to publish by checking the corresponding tree node check boxes. If you want to create one Web service (.asmx) for all of the selected receive ports instead of one Web service for each receive port, select the **Merge all selected ports into a single web service** option, and then click **Next**.  
  
    > [!NOTE]
    >  When you merge all selected ports into a single web service, the all selected ports have the same port type, and the operations names in the ports are unique.  
  
6.  On the **Web Service Properties** page, in the **Target namespace of the web service** box, type a target namespace for the Web service, select the appropriate boxes to specify how the wizard should handle SOAP headers and SharePoint Portal Server 2007 Single Sign-On (SSO) support for the Web service. If you want to further customize the Web service implementation, click **Advanced** button. It will show more available options:  
  
    |Option|Value|Description|  
    |------------|-----------|-----------------|  
    |SOAP Parameter Style|Default|This option specifies how parameters are formatted in a SOAP message. For more information, see SoapParameterStyle Enumeration at [http://go.microsoft.com/fwlink/?LinkId=62259](http://go.microsoft.com/fwlink/?LinkId=62259).|  
    |SOAP Parameter Style|Bare|This option specifies how parameters are formatted in a SOAP message. For more information, see SoapParameterStyle Enumeration at [http://go.microsoft.com/fwlink/?LinkId=62259](http://go.microsoft.com/fwlink/?LinkId=62259).|  
    |SOAP Parameter Style|Wrapped|This option specifies how parameters are formatted in a SOAP message. For more information, see SoapParameterStyle Enumeration at [http://go.microsoft.com/fwlink/?LinkId=62259](http://go.microsoft.com/fwlink/?LinkId=62259).|  
    |Conformance Claims|None|This option specifies the Web Services Interoperability (WSI) specification to which the binding claims to conform. For more information, see WebServiceBindingAttribute.ConformsTo Property at [http://go.microsoft.com/fwlink/?LinkId=193064](http://go.microsoft.com/fwlink/?LinkId=193064).|  
    |Conformance Claims|WS-I Basic Profile 1.1|This option specifies the Web Services Interoperability (WSI) specification to which the binding claims to conform. For more information, see WebServiceBindingAttribute.ConformsTo Property at [http://go.microsoft.com/fwlink/?LinkId=193064](http://go.microsoft.com/fwlink/?LinkId=193064).|  
    |Force Request Response|[Default]|This option specifies whether one-way BizTalk operations should be exposed as request-response web methods. Default is not force the on-way flag.|  
    |Force Request Response|No|This option specifies whether one-way BizTalk operations should be exposed as request-response web methods. Default is not force the on-way flag.|  
    |Force Request Response|Yes|This option specifies whether one-way BizTalk operations should be exposed as request-response web methods. Default is not force the on-way flag.|  
  
7.  On the **Web Service Properties** page, click **Next**.  
  
    > [!NOTE]
    >  The selection any of the SOAP header options are applied globally to all Web services and Web methods that are created when running this instance of the wizard.  
  
8.  If you selected **Add additional SOAP headers** option, the **Request SOAP Headers** and **Response SOAP Headers** pages appear. You can add and remove request and response SOAP headers using the **Add** and **Remove** buttons in the following dialog boxes:  
  
    -   To add a SOAP header, click **Add**. In the **BizTalk assembly file (\*.dll)** text box, type or browse for the assembly containing the SOAP header schema. The **Available schema types** list view displays each root element of the schema. Select a root node to add as a request or response SOAP header. To select multiple items, hold the CTRL key and click **OK**.  
  
    -   To remove a SOAP header from the list, select it from the list of added SOAP headers, and then click **Remove**.  
  
    -   Click **Next** on each **SOAP Header** page to continue the wizard.  
  
    > [!NOTE]
    >  A target namespace and root element name defines a SOAP header.  
  
    > [!NOTE]
    >  If the same combination of target namespace/root element name is added as a request and response SOAP header, it will not be treated as an in/out header. You must manually copy the incoming header to the outgoing header inside of an orchestration.  
  
    > [!NOTE]
    >  The same combination of target namespace/root element name can only be added once as a request SOAP header and once as a response SOAP header.  
  
9. On the **Web Service Project** page, in the **Project name** text box, type the name for the project. You can accept the default location (`http://localhost/<project_name>`), type a location for the project in the **Project location** text box, or click **Browse** and select a Web directory. Select any of the following options:  
  
    -   **Overwrite existing project.** This option is only available if the project location already exists. You will only be able to publish to the same location if you select this option. Otherwise, you must enter a different project location.  
  
    -   **Allow anonymous access to web service.** This option adds anonymous access to the created virtual directory. By default, the virtual directory inherits the access privileges from its parent virtual directory or the Web site (if it is a top-level virtual directory).  
  
    -   **Create BizTalk receive locations.** This option automatically creates the SOAP adapter receive ports and locations that correspond to each generated .asmx file. If a receive location already exists, it is not replaced. Receive locations for the SOAP adapter are resolved using the format /\<*virtual directory name*\>/\<*orchestration namespace_typename_portname*\>.asmx. After selecting this option, choose the application where the receive ports and locations will be generated.  
  
        > [!NOTE]
        >  The project location can exist on a different server. To publish a Web service to a different server, type the project name as `http://<servername>/<project_name>`.  
  
        > [!NOTE]
        >  The project location can exist on a non-default Web site. When publishing to a non-default Web site, include the port number of the Web site in the URL. For example, `http://localhost:8080/<project_name>`.  
  
        > [!NOTE]
        >  When using the wizard to create receive locations, the wizard creates the receive locations using the default values. The default value for the receive pipeline is the **Microsoft.BizTalk.DefaultPipelines.PassThruReceive** pipeline. If messages received through the published Web service require any special pipeline processing (for example, validation, correlation / property promotion, or inbound/outbound maps) then you should set the receive pipeline to **Microsoft.BizTalk.DefaultPipelines.XMLReceive**, or to a custom pipeline.  
  
        > [!NOTE]
        >  When you consume (call) Web services from an orchestration, the SOAP adapter only supports pass-through style send pipelines. You can use a custom send pipeline, but it cannot contain components that modify the body parts of the message. These components include the XML Assembler and any encoding components.  
  
        > [!NOTE]
        >  When you reach this page and if you choose to back out from choosing **Publishing schemas as web services** option, in the **Web Services** page, you may see the **Web service description** displays the service and method names from the BizTalk assembly previous selected before you back out from **Publish BizTalk orchestrations as web services** option. This is because the in-memory web service description is not cleared when the publishing method is changed.  
  
10. Click **Next** to review your settings for the ASP.NET Web service project.  
  
11. Click **Create** to create the ASP.NET Web service.  
  
12. Click **Finish** to complete the BizTalk Web Services Publishing Wizard.  
  
> [!NOTE]
>  If you are publishing an orchestration as a web service on Windows Vista, you must update the virtual directory hosting the service. To do so, issue the following command from the command prompt, replacing \<vdir\> with the name of the virtual directory: **%systemroot%\system32\inetsrv\APPCMD.EXE migrate config "Default Web Site/\<vdir name\>"**.  
  
## See Also  
 [Publishing an Orchestration as a Web Service](../core/publishing-an-orchestration-as-a-web-service.md)   
 [How to Map Orchestrations to Web Services](../core/how-to-map-orchestrations-to-web-services.md)