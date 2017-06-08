---
title: "Using SOAP Headers | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SOAP headers"
  - "SOAP headers, about SOAP headers"
  - "Web services, SOAP headers"
ms.assetid: 816618ff-ecd8-4f12-b9a9-dbe4203411d8
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using SOAP Headers
Microsoft BizTalk Server provides support for defined and unknown SOAP headers. Defined SOAP headers are headers in the Web Service Description Language (WSDL) that are explicity stated in the Web service. Unknown SOAP headers are headers that in the WSDL that are not explicity stated in the Web service. For more information about using SOAP headers, see "Using SOAP Headers" in the Microsoft .NET Framework documentation at [http://go.microsoft.com/fwlink/?LinkId=25363](http://go.microsoft.com/fwlink/?LinkId=25363).  
  
 BizTalk Server creates a context property for each defined SOAP header in the Web service.  
  
> [!NOTE]
>  Consumed Web services support only defined SOAP headers.You cannot set unknown headers when consuming Web services.  
  
## In This Section  
  
-   [SOAP Headers with Consumed Web Services](../core/soap-headers-with-consumed-web-services.md)  
  
-   [SOAP Headers with Published Web Services](../core/soap-headers-with-published-web-services.md)