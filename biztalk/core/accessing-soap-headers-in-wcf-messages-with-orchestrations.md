---
description: "Learn more about: Accessing SOAP Headers in WCF Messages with Orchestrations"
title: "Accessing SOAP Headers in WCF Messages with Orchestrations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords:
  - "orchestrations, SOAP headers [WCF services]"
  - "orchestrations, WCF services"
  - "WCF services, SOAP headers"
  - "SOAP headers, WCF messages"
ms.assetid: fe02fb02-18d6-4fc6-89e0-b06bdbfa5cb4
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Accessing SOAP Headers in WCF Messages with Orchestrations
To access the SOAP header values of incoming WCF messages in orchestrations, you use the context property **WCF.InboundHeaders**. The WCF adapters copy custom SOAP headers and standard SOAP headers in the inbound messages to the **WCF.InboundHeaders** property. The WCF adapters also allow you to select the properties you would like to promote or write to the context properties programmatically. See [SOAP Headers with Published WCF Services](../core/soap-headers-with-published-wcf-services.md) for more details.

 The value contained in the context property is a string containing XML data with the \<**headers**\> root element, and the incoming SOAP headers are copied as child elements of the \<**headers**\> element. The simplest way to access this data is to use the BizTalk Expression Editor in a **Message Assignment** or **Expression** shape, load the string in an **XmlDocument**, and use XPath queries to access specific fields. For more information about creating XML documents in the BizTalk Expression Editor, see [XLANG-s Language](../core/xlang-s-language.md).

 The following code example gets the request SOAP header in a **Message Assignment** or **Expression** shape for the **WCF.InboundHeaders** property:

```
stringVar = inboundMessageInstance(WCF.InboundHeaders);
```

 Context properties are associated with a particular message. The Messaging Engine does not automatically map the values of the SOAP headers from the request message to the response message. When creating the response message for a WCF service, you must specifically set the SOAP header values through the **WCF.OutboundCustomHeaders** property. The following command is the simplest method of setting a SOAP header context property:

```
outboundMessageInstance(WCF.OutbounCustomHeaders) = "<headers><Origination xmlns=\"http://SOAPHeaderSchemas.OrigDestSOAPHeader\">Home</Origination><Destination xmlns=\"http://SOAPHeaderSchemas.OrigDestSOAPHeader\">Work</Destination></headers>"
```

 You can also set the context property by creating an **XmlDocument** and writing the string value of the **XmlDocument** to the context property.

 For more information about how to access SOAP headers with the WCF adapters, see the SDK sample "Using Custom SOAP Headers with the WCF Adapters" at [http://go.microsoft.com/fwlink/?LinkId=79960](https://go.microsoft.com/fwlink/?LinkId=79960).

## See Also
 [Accessing SOAP Headers in WCF Messages with Pipeline Components](../core/accessing-soap-headers-in-wcf-messages-with-pipeline-components.md)
 [WCF Adapters Property Schema and Properties](../core/wcf-adapters-property-schema-and-properties.md)
 [SOAP Headers with Consumed WCF Services](../core/soap-headers-with-consumed-wcf-services.md)
