---
description: "Learn more about: Accessing SOAP Headers in WCF Messages with Pipeline Components"
title: "Accessing SOAP Headers in WCF Messages with Pipeline Components"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Accessing SOAP Headers in WCF Messages with Pipeline Components
To access the SOAP headers with the WCF adapters in pipeline components, you use a combination of the context property name, **InboundHeaders**, and the target namespace `http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties`. The WCF adapters copy custom SOAP headers and standard SOAP headers in the inbound messages to the **InboundHeaders** property. The WCF adapters also allow you to programmatically select the properties you would like to promote or write to the context properties programmatically. See [SOAP Headers with Published WCF Services](../core/soap-headers-with-published-wcf-services.md) for more details.

 The value contained in the context property is a string containing XML data with the \<**headers**\> root element, and the incoming SOAP headers are copied as child elements of the \<**headers**\> element. For more information about how to access SOAP headers with the WCF adapters, see the SDK sample "Using Custom SOAP Headers with the WCF Adapters" at [https://go.microsoft.com/fwlink/?LinkId=79960](https://go.microsoft.com/fwlink/?LinkId=79960).

 The following code from a custom pipeline component gets the request SOAP header in a receive pipeline component for the **InboundHeaders** property:

```
public IBaseMessage Execute(IPipelineContext pc, IBaseMessage inmsg)
{
   try
   {
   string stringVar = inmsg.Context.Read("InboundHeaders",    "http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties").ToString();
   }
   catch (Exception ex)
   {
   throw new Exception("Pipeline component exception - " + ex.Message);
   }
return inmsg;
}
```

 For more information about pipeline components, see [Developing Custom Pipeline Components](../core/developing-custom-pipeline-components.md).

## See Also
 [Accessing SOAP Headers in WCF Messages with Orchestrations](../core/accessing-soap-headers-in-wcf-messages-with-orchestrations.md)
 [WCF Adapters Property Schema and Properties](../core/wcf-adapters-property-schema-and-properties.md)
 [SOAP Headers with Consumed WCF Services](../core/soap-headers-with-consumed-wcf-services.md)
