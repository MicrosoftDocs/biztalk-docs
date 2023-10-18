---
description: "Learn more about: SOAP Headers with Consumed WCF Services"
title: "SOAP Headers with Consumed WCF Services"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# SOAP Headers with Consumed WCF Services
To send a message to a WCF service with the custom SOAP headers, these headers must be set in your orchestrations (in the Expression shape, for example) and pipeline components (in code) as the context property **OutboundCustomHeaders**. This context property is in the target namespace `http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties`, and contains string representations of the custom SOAP headers.  
  
 The data in the following XML outgoing message shows an example of the string representation of custom SOAP headers for the **OutboundCustomHeaders** property:  
  
```  
<headers>  
<Origination xmlns="http://SOAPHeaderSchemas.OrigDestSOAPHeader">Home</Origination>  
<Destination xmlns="http://SOAPHeaderSchemas.OrigDestSOAPHeader">Work</Destination>  
</headers>  
```  
  
 Inbound SOAP headers also contain string representations of the SOAP headers. The values are similar to creating a request SOAP header.  
  
## In This Section  
  
-   [Using SOAP Headers in WCF Messages with Orchestrations](../core/using-soap-headers-in-wcf-messages-with-orchestrations.md)  
  
-   [Using SOAP Headers in WCF Messages with Pipeline Components](../core/using-soap-headers-in-wcf-messages-with-pipeline-components.md)  
  
## See Also  
 [WCF Adapters Property Schema and Properties](../core/wcf-adapters-property-schema-and-properties.md)   
 [SOAP Headers with Published WCF Services](../core/soap-headers-with-published-wcf-services.md)
