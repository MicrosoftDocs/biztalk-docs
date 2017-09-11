---
title: "Using Web Services | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Web services"
  - "Web services, about Web services"
  - "orchestrations, Web services"
  - "Web services, orchestrations"
ms.assetid: a54261e3-d8ef-4770-8d9a-147685846051
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using Web Services
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides built-in support for Web services. BizTalk Server enables the reuse and aggregation of all your existing Web services within your orchestrations. You can also publish (expose) your orchestrations as Web services to separate the Web service logic from the business process logic.  
  
 BizTalk Server implements support for native adapters in Web services. Native adapter support provides scalability, fault tolerance, and tracking capabilities for Web services without writing a single line of code. For information about the SOAP adapter, see [SOAP Adapter](../core/soap-adapter.md).  
  
 The Web services support in BizTalk Server falls into two categories: consuming or calling Web services and publishing or creating Web services.  
  
 Before you consume or publish a Web service, you should have an understanding of XML Web services in ASP.NET. For information about the basics of XML Web services, see the article "XML Web Services Basics" at [http://go.microsoft.com/fwlink/?LinkId=193057](http://go.microsoft.com/fwlink/?LinkId=193057).  
  
 **Consuming Web services**  
  
 You can consume (call) Web services from within an orchestration. You can aggregate several Web services into single orchestration to complete an entire business process.  
  
 **Publishing Web services**  
  
 You can publish Web services using the BizTalk Web Services Publishing Wizard. Orchestrations and send adapters can use these published Web services.  
  
 **Using SOAP headers**  
  
 BizTalk Server provides support for defined and unknown SOAP headers. BizTalk Server creates a context property for each defined SOAP header in the Web service.  
  
 **Web Services standards**  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] should work with any Web Services standards when sending and receiving. Not all standards have been tested. Typically, the standards supported by WCF are also supported by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Sample standards include:  
  
-   WS-ReliableMessaging  
  
-   WS-Security  
  
-   WS-SecureConversation  
  
-   WS-Trust  
  
-   WS-Federation  
  
-   WS-Addressing  
  
-   WS-Policy  
  
-   WS-MetadataExchange  
  
-   WS-Coordination  
  
-   WS-Atomic  
  
## In This Section  
  
-   [Consuming Web Services](../core/consuming-web-services.md)  
  
-   [Publishing Web Services](../core/publishing-web-services.md)  
  
-   [Using SOAP Headers](../core/using-soap-headers.md)