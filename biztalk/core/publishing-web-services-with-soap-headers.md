---
description: "Learn more about: Publishing Web Services with SOAP Headers"
title: "Publishing Web Services with SOAP Headers"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Publishing Web Services with SOAP Headers
You add SOAP headers to your Web services when you run the BizTalk Web Services Publishing Wizard. When you publish a Web service that supports SOAP headers, the headers become available to orchestrations and pipeline components as context properties that contain string representations of the SOAP headers.  
  
## Defined SOAP headers  
 When you add a defined SOAP header using the wizard, the wizard creates a context property with a name that corresponds to the root element of the SOAP header. All defined SOAP header context properties have the namespace `http://schemas.microsoft.com/BizTalk/2003/SOAPHeader`. When the SOAP adapter converts the SOAP request to a BizTalk message, it creates one SOAP header context property.  
  
 The following example shows a simple SOAP request:  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
       <soap:Header>  
             <OrigDest xmlns="http://SOAPHeaderWS.ItemAvailability">  
                    <Origination>Work</Origination>  
                    <Destination>Home</Destination>  
             </OrigDest>  
       </soap:Header>  
       <soap:Body>  
  
       </soap:Body>  
</soap:Envelope>  
```  
  
 For the simple SOAP request, the SOAP adapter created a BizTalk message with one SOAP header context property **OrigDest** and the string.  
  
 The following example shows the string created by the SOAP adapter:  
  
```  
"<?xml version="1.0" encoding="utf-16"?><OrigDest xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://SOAPHeaderSchemas.OrigDestSOAPHeader"><Origination xmlns="">Home</Origination><Destination xmlns="">Work</Destination> </OrigDest>"  
```  
  
## Unknown SOAP headers  
 If you choose to support unknown SOAP headers in the wizard, the wizard creates a context property with the name **UnknownHeaders** and the namespace `http://schemas.microsoft.com/BizTalk/2003/soap-properties`. The **UnknownHeaders** context property contains all of the received unknown SOAP headers.  
  
 For example, if you receive an unknown SOAP header with the root element name, **CustomerGroup**, the **UnknownHeaders** context property contains the string:  
  
```  
"<?xml version="1.0" encoding="utf-16"?><UnknownHeaders><CustomerGroup xmlns="http://SOAPHeaderWS/CustomerGroup"><Id xmlns="">My Customer</Id>  
</CustomerGroup></UnknownHeaders>"  
```  
  
 For more information about adding defined SOAP headers or supporting unknown SOAP headers, see [Publishing an Orchestration as a Web Service](../core/publishing-an-orchestration-as-a-web-service.md). Also see [Publishing Schemas as a Web Service](../core/publishing-schemas-as-a-web-service.md).  
  
## See Also  
 [SOAP Headers with Published Web Services](../core/soap-headers-with-published-web-services.md)
