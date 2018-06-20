---
title: "Considerations When Publishing Web Services | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "schemas, publishing"
  - "Web services, planning"
  - "Web services, schemas"
  - "schemas, Web services"
ms.assetid: 3ace0260-a1cb-4e59-a820-36ee7d5cceda
caps.latest.revision: 21
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Considerations When Publishing Web Services
This topic provides information that you should consider before you publish your Web services.  
  
## Publishing schemas and the include element  
 There are a few scenarios where schemas that contain the **include** element cannot be published as a Web service. An error will occur when you complete the BizTalk Web Services Publishing Wizard. These restrictions include the following:  
  
- Circular includes (the included schema has an **include** element to the including schema)  
  
- An unresolved **schemaLocation** attribute will cause an error  
  
  For more information about the limitation of include element, see "Include Element Binding Support" at [http://go.microsoft.com/fwlink/?LinkId=62312](http://go.microsoft.com/fwlink/?LinkId=62312).  
  
## Publishing schemas and the import element  
 BizTalk Web Services Publishing Wizard has the same limitation as XSD.exe included in .NET Framework. For more information, see "Import Element Binding Support" at [http://go.microsoft.com/fwlink/?LinkId=62311](http://go.microsoft.com/fwlink/?LinkId=62311).  
  
## Publishing schemas and the redefine element  
 BizTalk Web Services Publishing Wizard has the same limitation as XSD.exe included in .NET Framework. For more information, see "Redefine Element Binding Support" at [http://go.microsoft.com/fwlink/?LinkId=62313](http://go.microsoft.com/fwlink/?LinkId=62313).  
  
## Publishing schemas that specify values for minOccurs or maxOccurs attributes  
 If you publish a schema that contains **minOccurs** or **maxOccurs** attributes with specific values, these values may be different in schema exposed by the published Web service. As a general rule of thumb, all minOccurs attributes are converted to 0 (minOccurs=0) and maxOccurs attributes are converted to either 1 or unbounded (maxOccurs=1 or maxOccurs=unbounded).  
  
## Publishing envelope schemas  
 If you have an envelop schema that you are publishing as a Web service, you need to manually modify the generated Web project.  
  
#### To modify the generated Web project for envelope schemas  
  
1.  Open the <`myWebService`>.asmx.cs file.  
  
2.  Edit the file and change `bodyTypeAssemblyQualifiedName = <dll.name.version.>` to `bodyTypeAssemblyQualifiedName = null`.  
  
> [!NOTE]
>  You may need to reset Internet Information Services (IIS) if the previous .dll file is still in the ASPNET worker process.  
  
## Web service and Web method attributes  
 The BizTalk Web Services Publishing Wizard does not allow you to customize the Web service or Web method attributes you use in ASP.NET. Some attributes are automatically set based upon information that the wizard provides. The wizard does not use the other attributes.  
  
 Modifying the existing attributes or adding new attributes to Web services that the BizTalk Web Services Publishing Wizard generates may cause the Web service to function incorrectly.  
  
 For more information about Web services and Web method attributes, see the **WebServiceAttribute** and **WebMethodAttribute** classes in the .NET Framework SDK documentation.  
  
## Web method required  
 A Web service must have at least one Web method. Without at least one Web method, port types will not have their operations created. XLANG/s does not support port types that do not have operations.  
  
## DBCS character support  
 Web services do not support Chinese/Japanese/Korean (CJK) Unified Ideograph Extension A characters.  
  
## Republishing Web services using the BizTalk Web Services Publishing Wizard  
 You can use the BizTalk Web Services Publishing Wizard to republish a published Web service. On the **Web**<strong>Service</strong>**Project** page, you can select the **Overwrite**<strong>Web</strong>**Service** option.  
  
 The wizard does not store previously used settings. If you make changes in the settings when you rerun the wizard, any Web clients that consume (call) the published Web service may fail. You should update the Web references of any clients that consume (call) a republished Web service.  
  
## Clients of published Web services may not receive Server script timeout errors  
 Web services generated with the Web Services Publishing Wizard in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] are configured by default with a script timeout value of **110** seconds. This is the default value for the .NET Framework. **HttpServerUtility.ScriptTimeout** property. Web clients that use .NET Framework are configured by default with a request timeout value of **100** seconds. This is the default value for the .NET Framework **HttpWebRequest.Timeout** property.  
  
 If Web clients that use .NET framework are calling a Web Service generated with the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Web Services Publishing Wizard, it is possible that the client cannot receive server script timeout errors because the client request timeout occurs first by default. To resolve this problem you can do one of the following:  
  
-   Increase the client request timeout to a value greater than the server script timeout by increasing the value for the **HttpWebRequest.Timeout** property on the client.  
  
-   Reduce the server script timeout to a value less than the client request timeout by reducing the value for the **HttpServerUtility.ScriptTimeout** property on the server.  
  
## See Also  
 [Publishing Web Services](../core/publishing-web-services.md)