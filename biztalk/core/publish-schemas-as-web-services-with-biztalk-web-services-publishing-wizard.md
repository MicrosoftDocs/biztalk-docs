---
title: "How to Use the BizTalk Web Services Publishing Wizard to Publish Schemas as a Web Service | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BizTalk Web Services Publishing Wizard, publishing"
  - "BizTalk Web Services Publishing Wizard, schemas"
ms.assetid: b22de720-1416-486a-988f-e52527ad9ab1
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Use the BizTalk Web Services Publishing Wizard to Publish Schemas as a Web Service
You use the BizTalk Web Services Publishing Wizard to publish schemas as a Web service.  
  
### To publish schemas as a Web service  
  
1. Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Web Services Publishing Wizard**.  
  
   > [!IMPORTANT]
   >  You must build BizTalk projects prior to running the BizTalk Web Services Publishing Wizard.  
  
2. On the **Welcome** page, click **Next**.  
  
3. On the **Create Web Service** page, select **Publish schemas as web services** and then click **Next**.  
  
4. On the **Web Service** page, define the Web service(s) to publish. You use the tree in the **Web service description** dialog box to add, remove, rename, and edit the Web service description nodes. The **Information** dialog box provides information about the selected node and displays any errors in the current node or any sub nodes:  
  
   -   The root node to the tree (Web service description) describes the Web service project name. The virtual directory name uses the root node as the default name. You can modify the Web service description by selecting **Rename web service description**.  
  
   -   To add a new Web service, right-click the **Web service description** node, and then click **Add web service**. This creates a new Web service without any Web methods. To modify the name of the Web service, right-click the Web service node, and select **Rename web service**,and then press Enter to accept the new name.  
  
   -   To add a new Web method, right-click the Web service node, point to **Add Web Method**, and then click **One-way** (for a request Web method) or **Request-response** (for a request-response Web method) from the shortcut menu.  
  
   -   To set the request and response schema types, right-click the **Request** or **Response** node, and then click **Select schema type**. In the **Request Message Type** dialog box, type the name of the assembly containing the document schema in the **BizTalk assembly file** text box or click **Browse** to search for the assembly. The **Available schema types** list view displays each root element of the schema. Select a root node to add as the request or response schema type.  
  
       > [!NOTE]
       >  If you installed the BizTalk assembly file into the Global Assembly Cache (GAC), make sure that the assembly in the GAC has been updated with the assembly that you will select in the **Request Message Type** dialog box. If the GAC has the same fully qualified name, the BizTalk Web Services Publishing Wizard uses the assembly file in the GAC instead of the one you selected.  
  
   -   You can rename the **Request** and **Response** nodes without affecting the generated code. After defining your schemas, you can rename the part elements, which modifies the Web method parameter name. You can see the changes by viewing the generated Web service code.  
  
   > [!NOTE]
   >  You cannot use spaces when renaming any of the Web service description nodes.  
  
5. Click **Next** to continue the wizard.  
  
6. On the **Web Service Properties** page, in the **Target namespace of web service** dialog box, type a target namespace for the Web service, and select the appropriate boxes to specify how the wizard should handle SOAP headers and Single Sign-On support for the Web service. If you want to further customize the Web service implementation, click **Advanced** button. It will show more available options:  
  
   |Option|Value|Description|  
   |------------|-----------|-----------------|  
   |SOAP Parameter Style|Default|This option specifies how parameters are formatted in a SOAP message. For more information, see SoapParameterStyle Enumeration at [http://go.microsoft.com/fwlink/?LinkId=62259](http://go.microsoft.com/fwlink/?LinkId=62259).|  
   |SOAP Parameter Style|Bare|This option specifies how parameters are formatted in a SOAP message. For more information, see SoapParameterStyle Enumeration at [http://go.microsoft.com/fwlink/?LinkId=62259](http://go.microsoft.com/fwlink/?LinkId=62259).|  
   |SOAP Parameter Style|Wrapped|This option specifies how parameters are formatted in a SOAP message. For more information, see SoapParameterStyle Enumeration at [http://go.microsoft.com/fwlink/?LinkId=62259](http://go.microsoft.com/fwlink/?LinkId=62259).|  
   |Conformance Claims|None|This option specifies the Web Services Interoperability (WSI) specification to which the binding claims to conform. For more information, see WebServiceBindingAttribute.ConformsTo Property at [http://go.microsoft.com/fwlink/?LinkId=193064](http://go.microsoft.com/fwlink/?LinkId=193064).|  
   |Conformance Claims|WS-I Basic Profile 1.1|This option specifies the Web Services Interoperability (WSI) specification to which the binding claims to conform. For more information, see WebServiceBindingAttribute.ConformsTo Property at [http://go.microsoft.com/fwlink/?LinkId=193064](http://go.microsoft.com/fwlink/?LinkId=193064).|  
   |Force Request Response|[Default]|This option specifies whether one-way BizTalk operations should be exposed as request-response web methods. Default is not force the on-way flag.|  
  
   > [!NOTE]
   >  The selection any of the SOAP header options are applied globally to all Web services and Web methods created when running this instance of the wizard.  
  
7. On the **Web Service Properties** page, click **Next**.  
  
8. If you selected **Add additional SOAP headers**, the **Request SOAP Headers** and **Response SOAP Headers** pages appear. You can add and remove request and response SOAP headers using the **Add** and **Remove** buttons in the following dialog boxes:  
  
   -   To add a SOAP header, click **Add**. In the **BizTalk assembly name (\*.dll)** text box, type the assembly name or browse for the assembly containing the SOAP Header schema in the **BizTalk assembly file** text box. The **Available schema types** list view displays each root element of the schema. Select a root node to add as a request or response SOAP header. To select multiple items, hold the CTRL key and click **OK**.  
  
   -   To remove a SOAP header from the list, select it from the list of added SOAP headers, and then click **Remove**.  
  
   -   Click **Next** on each SOAP header page to continue the wizard.  
  
   > [!NOTE]
   >  The target namespace and root element name define the SOAP header.  
  
   > [!NOTE]
   >  If the same combination of target namespace/root element name is added as a request and response SOAP header, it will not be treated as an in/out header. You must manually copy the incoming header to the outgoing header inside of an orchestration.  
  
   > [!NOTE]
   >  The same combination of target namespace/root element name can only be added once as a request SOAP header and once as a response SOAP header.  
  
9. On the **Web Service Project** page, in the **Project location** text box, type the project location. You can accept the default location (http://localhost/<*project_name*>), type a location for the project, or click **Browse** and select a Web directory. Select any of the following options:  
  
    -   **Overwrite existing project.** This option is only available if the project location already exists. You will only be able to publish to the same location if you select this option. Otherwise, you must enter a different project location.  
  
    -   **Allow anonymous access to web service.** This option adds anonymous access to the created virtual directory. By default, the virtual directory inherits the access privileges from its parent virtual directory or the Web site (if it is a top-level virtual directory).  
  
    -   **Create BizTalk receive locations.** This option automatically creates the SOAP adapter receive ports and locations that correspond to each generated .asmx file. If another receive location already exists, the receive location is not be replaced. Receive locations for the SOAP adapter are resolved using the format "/\<*virtual directory name*\>/\<*orchestration namespace_typename_portname*\>.asmx". After selecting this option, choose the application where the receive ports and locations will be generated.  
  
        > [!NOTE]
        >  The project location can exist on a different server. To publish a Web service to a different server, type the project name as **http://<*servername*>/<*project_name*>**.  
  
        > [!NOTE]
        >  The project location can exist on a non-default Web site. When publishing to a non-default Web site, include the port number of the Web site in the URL: http://localhost:8080/<*project_name*>.  
  
        > [!NOTE]
        >  When you use the wizard to create receive locations, the wizard creates the receive locations using many default values. The default values for receive and send pipelines are **Microsoft.BizTalk.DefaultPipelines.PassThruReceive** and **Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**. If messages received through the published Web service require any special pipeline processing (for example, validation, correlation, or inbound/outbound maps), then you should set the send and receive pipelines to **Microsoft.BizTalk.DefaultPipelines.XMLReceive**, **Microsoft.BizTalk.DefaultPipelines.XMLSend**, or to a custom pipeline.  
  
10. Click **Next** to review your settings for the ASP.NET Web service project.  
  
11. Click **Create** to create the ASP.NET Web service.  
  
12. Click **Finish** to complete the BizTalk Web Services Publishing Wizard.  
  
## See Also  
 [Publishing Schemas as a Web Service](../core/publishing-schemas-as-a-web-service.md)