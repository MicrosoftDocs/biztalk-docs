---
description: "Learn more about: Consuming Web Services with SOAP Headers"
title: "Consuming Web Services with SOAP Headers | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SOAP headers, consuming"
  - "Web services, consuming"
  - "Web services, SOAP headers"
  - "SOAP headers, Web services"
ms.assetid: c2dfe7d8-e2f0-4bc6-b79c-354d06a7ffd6
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Consuming Web Services with SOAP Headers
After you consume a Web service with defined SOAP headers, these headers become available to your orchestrations and pipeline components as context properties. These context properties contain string representations of the SOAP headers. For each defined SOAP header in the Web service, you can create a context property by using the name that corresponds to the root element of the SOAP header. All defined SOAP header context properties are in the `http://schemas.microsoft.com/BizTalk/2003/SOAPHeader` namespace.  
  
 The following example shows how to create a SOAP header context property **OrigDest** using the SOAP header example in [SOAP Headers with Consumed Web Services](../core/soap-headers-with-consumed-web-services.md):  
  
```  
<?xml version="1.0" encoding="utf-16"?>  
<OrigDest xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns=" http://SOAPHeaderWS.ItemAvailability">  
   <Origination xmlns="">Home</Origination>  
      <Destination xmlns="">Work</Destination>  
</OrigDest>  
```  
  
 Response SOAP headers also contain string representations of the defined SOAP header. The values are similar to creating a request SOAP header.  
  
## See Also  
 [SOAP Headers with Consumed Web Services](../core/soap-headers-with-consumed-web-services.md)
