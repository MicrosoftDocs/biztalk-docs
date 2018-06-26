---
title: "Adding Web References | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BPEL, orchestrations"
  - "orchestrations, BPEL"
  - "Web services, ports"
  - "orchestrations, exporting"
  - "Web services, projects"
  - "Web services, references"
  - "projects, Web services"
ms.assetid: 7e40f215-f11a-4151-bcc6-e107bf36b6f6
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Adding Web References
Before you can add a Web port, you need to add a Web reference to your BizTalk project. A Web reference is a description of a Web service that is available to your project. When you add a Web reference to your project, BizTalk project creates an orchestration Web port type, Web message types, Reference.map (map file), Reference.odx (orchestration file), \<*WebService*\>.disco (discovery file), and \<*WebService*\>.wsdl (Web Service Description Language file) to your project. If your Web Service Description Language (WSDL) file contains schema Web message types, BizTalk project adds Reference.xsd to your project.  
  
 A Web reference includes:  
  
- A Universal Resource Locator (URL) for the Web service.  
  
- A WSDL file that offers information about the service such as available methods, ports, and message types.  
  
- A reference map (Reference.map).  
  
  When you add a Web reference, all the Web methods for that Web service must be compatible with BizTalk Server. You cannot specify conditional attributes for specific Web methods in a Web service.  
  
  You add a Web reference to your project by using the **Add Web Reference** dialog box. For more information about adding Web references, see [Using Visual Studio](../core/using-visual-studio.md).  
  
  If you are planning to export your orchestration using the Business Process Execution Language (BPEL) export process, you cannot reference a Web reference from an existing BizTalk project. When you reference a Web reference from an existing BizTalk project, the BPEL export process will auto-generate a second WSDL file and you will lose your binding information.  
  
## See Also  
 [Creating Web Ports](../core/creating-web-ports.md)   
 [Consuming Web Services](../core/consuming-web-services.md)