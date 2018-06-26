---
title: "How to Map Orchestrations to Web Services | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "orchestrations, Web services"
  - "BizTalk Web Services Publishing Wizard, naming conventions"
  - "Web services, orchestrations"
  - "orchestrations, naming conventions"
  - "Web services, naming conventions"
ms.assetid: e6a58978-c81c-49f3-9428-9bff60f1ded7
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Map Orchestrations to Web Services
An orchestration can have multiple receive ports. Using the BizTalk Web Services Publishing Wizard, you select receive ports to publish as Web services. The wizard creates one Web service (.asmx file) for each receive port. The wizard can also create one Web service for all of the receive ports if they are the same receive port type (one-way or request/response). Operations become function calls. Each operation in the receive port becomes a Web method. Request operations become input parameters. Response operations become return types.  
  
 If the request and response operations are the same Web message type, the input parameter becomes a **ref** and the return type is **void**. ASP.NET Web clients may change the Web method signature by combining the in and out parameters of the same type. For example, an ASP.NET Web client may change a BizTalk Web method from **string myService(string part)** to **void myService(ref string part)**.  
  
 The operation message types define the Web method signatures. Each message type part is a parameter in the Web method.  
  
## Message type part names and target namespaces  
 Document schemas and user defined classes with **XmlRootAttribute** specified are message type parts that have defined target namespaces. EDI schemas, user-defined classes without **XmlRootAttribute** specified, and built-in types, such as **System.String** are message type parts without defined target namespaces.  
  
|If the message type part name has a|Parameter Name Used|  
|-----------------------------------------|-------------------------|  
|Defined target namespace|Root element name|  
|No defined target namespace|Message type part name|  
  
> [!NOTE]
>  When a multipart message type is used for the response message, the BizTalk Web Services Publishing Wizard uses the first message part for the return value and the remaining message parts are used as out parameters.  
  
## Orchestrations with multiple operations  
 If your orchestration has multiple operations, you should design your orchestrations to have one receive port instead of several receive ports. This design prevents the BizTalk Web Services Publishing Wizard from creating multiple Web service (.asmx) files and only works when all the operations have the same calling pattern—all one-way operations or all request-response operations. A single receive port cannot contain both one-way and request/response operations.  
  
> [!NOTE]
>  The BizTalk Web Services Publishing Wizard displays public receive ports. Public receive ports are port types with a public type modifier. You can publish only public ports as a Web service. The default port type is internal.  
  
> [!NOTE]
>  If your receive port is defined as one-way, the Web method response type is **void** and no information is returned to the Web client. Exceptions thrown by the SOAP adapter or an orchestration are not returned to the Web client.  
  
## Web services naming conventions for published orchestrations  
 The BizTalk Web Services Publishing Wizard generates Web service (.asmx) file names based on the orchestrations namespace, followed by an underscore (*), followed by the type name, followed by an underscore (\\*), and followed by the name of the receive port. An underscore (\_) replaces any of the parts that contain periods. The name of the Web service always has the port name appended.  
  
 The following table shows how the BizTalk Web Services Publishing Wizard generates Web service names.  
  
|Orchestration(s) with Web port(s)|Generated Web service name|  
|-------------------------------------------|--------------------------------|  
|One orchestration with one Web port|orchestration1_port1.asmx|  
|One orchestration with two Web ports|orchestration1_port1.asmx and orchestration1_port2.asmx|  
|Two orchestrations with one Web port each|orchestration1_port1.asmx and orchestration2_port2.asmx|  
  
## See Also  
 [Publishing an Orchestration as a Web Service](../core/publishing-an-orchestration-as-a-web-service.md)   
 [How to Use the BizTalk Web Services Publishing Wizard to Publish an Orchestration as a Web Service](../core/publish-orchestration-as-web-service--biztalk-web-services-publishing-wizard.md)