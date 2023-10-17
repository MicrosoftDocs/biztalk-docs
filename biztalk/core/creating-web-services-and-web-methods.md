---
description: "Learn more about: Creating Web Services and Web Methods"
title: "Creating Web Services and Web Methods"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Creating Web Services and Web Methods
When you publish schemas as a Web service, you control the creation of Web services and Web methods in the BizTalk Web Services Publishing Wizard. You can rename the Web service description, Web service and Web method inside the tree available on the Web Services page. You can add and remove Web services and Web methods. The wizard uses the root element names of the selected request schemas as the input parameter name. The Web method return value returns the response schema.  
  
> [!NOTE]
>  ASP.NET Web clients may change the Web method signature by combining the in and out parameters of the same type. For example, an ASP.NET Web client may change a BizTalk Web method from **string myService(string part)** to **void myService(ref string part)**.  
  
> [!NOTE]
>  If your receive port is defined as one-way, the Web method response type is **void** and no information is returned to the Web client. The SOAP adapter and orchestration do not return thrown exceptions to the Web client.  
  
## Web services naming conventions for published orchestrations  
 The BizTalk Web Services Publishing Wizard generates Web service (.asmx) file names based on the Web services description that you define in the Web Service page. The following table shows the default values for the Web service file names.  
  
|Generated Web service|File name|  
|---------------------------|---------------|  
|BizTalkWebService|Visual Studio Web Service project name|  
|WebService1|Web service (.asmx) file name|  
|WebMethod1|Web method name|  
  
 The generated Web service does not reflect the names of the remaining nodes.  
  
## See Also  
 [Publishing Schemas as a Web Service](../core/publishing-schemas-as-a-web-service.md)   
 [How to Use the BizTalk Web Services Publishing Wizard to Publish Schemas as a Web Service](../core/publish-schemas-as-web-services-with-biztalk-web-services-publishing-wizard.md)
