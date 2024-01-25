---
description: "Learn more about: Using SOAP Headers in WCF Messages with Pipeline Components"
title: "Using SOAP Headers in WCF Messages with Pipeline Components"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Using SOAP Headers in WCF Messages with Pipeline Components
You can set the custom SOAP headers with the WCF adapters in pipeline components. You use a combination of the context property name, **OutboundCustomHeaders**, and the target namespace `http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties`. When you use the **OutboundCustomHeaders** property, the property must have the \<**headers**\> element as the root element. All of the custom SOAP headers must be placed inside the \<**headers**\> element. If the custom SOAP header value is an empty string, you must assign \<**headers**\>\</**headers**\> or \<**headers**/\> to the **OutboundCustomHeaders** property. For more information about how to use SOAP headers with the WCF adapters, see the SDK sample, Using Custom SOAP Headers with the WCF Adapters, from [https://go.microsoft.com/fwlink/?LinkId=79960](https://go.microsoft.com/fwlink/?LinkId=79960).

 The following code example sets custom SOAP headers in a send pipeline component for a property named **OutboundCustomHeaders**:

```
public IBaseMessage Execute(IPipelineContext pc, IBaseMessage inmsg)
{
   try
      {
       string stringVar = "<headers>
             <Origination>Home</Origination>
             <Destination>Work</Destination>
          </headers>";
inmsg.Context.Write("OutboundCustomHeaders","http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties", stringVar);
      }
   catch (Exception ex)
      {
   throw new Exception("Pipeline component exception - " + ex.Message);
      }
return inmsg;
}
```

 For more information about pipeline components, see [Developing Custom Pipeline Components](../core/developing-custom-pipeline-components.md).

> [!NOTE]
>  You must not set the standard SOAP headers that the WCF infrastructure uses for Web services standards such as WS-Addressing, WS-Security, and WS-AtomicTransaction.

## See Also
 [Using SOAP Headers in WCF Messages with Orchestrations](../core/using-soap-headers-in-wcf-messages-with-orchestrations.md)
 [SOAP Headers with Consumed WCF Services](../core/soap-headers-with-consumed-wcf-services.md)
 [WCF Adapters Property Schema and Properties](../core/wcf-adapters-property-schema-and-properties.md)
 [SOAP Headers with Published WCF Services](../core/soap-headers-with-published-wcf-services.md)
