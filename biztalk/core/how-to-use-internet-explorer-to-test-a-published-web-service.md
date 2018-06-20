---
title: "Test BizTalk web service | Microsoft Docs"
description: Configure receive locations and web.config to test BizTalk web service in a web browser
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4dc2171d-4abe-43db-b4bc-e484048c6430
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Test a BizTalk Web Service

## Overview
You can test your published Web service without writing a Web client application. You can use a Web browser, such as Internet Explorer, to test your published Web service. Although you can access any published Web service using a Web browser, you can only test Web services with Web methods that contain simple type parameters. To test your Web method in a Web browser, your message parts for the request and response messages that are used in the receive port can only be a simple type, such as **System.String** or **System.Int32**. If any message part uses a schema as a message type, you cannot test the Web method with a browser.  
  
 If you want to test your published Web services using HTTP-GET or HTTP-POST, you must configure your BizTalk receive location for the SOAP adapter and modify the Web.config file for your published Web service.  
  
 **Modifying the Receive Locations**  
  
 When the SOAP adapter configures receive locations, the SOAP adapter normally sets the URI of the receive location by giving the virtual directory and the Web service .asmx file name:  
  
```  
/PurchaseOrder/POOrchestration.asmx  
```  
  
 This allows the SOAP adapter to receive Web service requests using the HTTP-SOAP protocol. To configure the receive location to use the HTTP-GET or HTTP-POST protocol, you must append the method name to the URI:  
  
```  
/PurchaseOrder/POOrchestration.asmx/Operation_1  
```  
  
 The method name is the same as the port operation name in the orchestration.  
  
 **Modifying the Web.config file**  
  
 By default, the wizard configures the Web services to use the HTTP-SOAP protocol. HTTP-GET and HTTP-POST are explicitly disabled. To test a Web service with a Web browser, you must enable HTTP-GET.  
  
## Update the Web.config
  
1. Open the Web.config file for the published Web service.  
  
   > [!NOTE]
   >  You can find the Web.config file in the directory that you configured for the IIS virtual root that contains the Web service.  
  
2. Find the \<protocols\> section:  
  
   ```  
   <webServices>  
      <protocols>  
        <remove name="HttpPost" />  
        <remove name="HttpGet" />  
        <remove name="HttpPostLocalhost" />  
      </protocols>  
  
   </webServices>  
   ```  
  
3. For testing HTTP-GET, HTTP-POST, or HTTP-POST from the local computer, remove the corresponding line from the \<protocols\> section.  
  
   For more information about the configuration options, see [Configuration Options for XML Web Services Created Using ASP.NET](https://msdn.microsoft.com/library/b2c0ew36.aspx). 
  
#### Access a Web service with Internet Explorer  
  
- In Internet Explorer, in the **Address** box, type the URL for the Web service using the format **http://<em>servername</em>/*apppath*/*webservicename*.asmx**.  
  
  |Parameter|Value|  
  |---------------|-----------|  
  |***servername***|The name of the server that you have deployed your XML Web service.|  
  |***Apppath***|The name of your virtual directory and the Web application path.|  
  |***webservicename.asmx***|The name of the XML Web service .asmx file.|  
  
  The description for the Web service shows you all the Web service methods that the particular Web service supports. The Web service description page contains links for each available Web method and the service description of the Web service.  
  
#### Test a Web service with Internet Explorer using HTTP-GET  
  
1.  After accessing the Web service description page, click one of the Web methods listed in the Web service description page.  
  
2.  Type the necessary parameters for the Web method, and then click **Invoke**.  
  
3.  The server returns an XML response in the browser. If the return data type for the Web service is a double-precision floating-point number, the result might look like the following:  
  
    ```  
    <?xml version="1.0" ?>  
    <double>74.5</double>  
    ```  
  
#### Test a Web service with Internet Explorer using HTTP-GET (alternate method)  
  
1.  In Internet Explorer, in the **Address** box, type the URL for the Web service using the format ***http://servername/vdir/webservicename.asmx/Methodname?parameter=value***.  
  
    |Parameter|Value|  
    |---------------|-----------|  
    |***servername***|The name of the server that you have deployed your XML Web service.|  
    |***Apppath***|The name of your virtual directory and the Web application path.|  
    |***webservicename.asmx***|The name of the XML Web service .asmx file.|  
    |***Methodname***|The name of a public method that the XML Web service exposes. If left blank, the description page for the XML Web service appears, listing each public method available in the .asmx file. (Optional)|  
    |***parameter***|The appropriate parameter name and value for any parameters required by your method. If left blank, the description page for the XML Web service appears, listing each public method available in the .asmx file. (Optional)|  
  
    > [!NOTE]
    >  The XML Web service method name in this syntax is case sensitive, but the server, project, and XML Web service names are not.  
  
2.  Press Enter. The Web browser displays an XML response from the server.  
  
    > [!NOTE]
    >  You can also use HTTP-POST to call the Web service. For information and samples about calling XML Web services from a Web browser, see [Access XML Web Services from a Browser](https://msdn.microsoft.com/library/45fez2a8.aspx).  
  
## See Also  
 [Testing Published Web Services](../core/testing-published-web-services.md)