---
description: "Learn more about: Consuming Web Services with SOAP Headers"
title: "Consuming Web Services with SOAP Headers"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
