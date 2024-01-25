---
description: "Learn more about: Using SOAP Headers in WCF Messages with Orchestrations"
title: "Using SOAP Headers in WCF Messages with Orchestrations"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Using SOAP Headers in WCF Messages with Orchestrations
To send the custom SOAP headers with outgoing WCF messages in orchestrations, you use the context property, **WCF.OutboundCustomHeaders**. The WCF adapters send the custom SOAP headers combined with the standard SOAP headers that the WCF infrastructure uses for Web services standards such as WS-Addressing, WS-Security, and WS-AtomicTransaction. When you use the **OutboundCustomHeaders** property, the property must have the \<**headers**\> element as the root element. All of the custom SOAP headers must be placed inside the \<**headers**\> element. If the custom SOAP header value is an empty string, you must assign \<**headers**\>\</**headers**\> or \<**headers**/\> to the **OutboundCustomHeaders** property.

 For orchestrations, the SOAP header context properties are set to strings that contain XML data. You set these strings by using BizTalk Expression Editor in a **Message Assignment** or **Expression** shape. For more information about how to use SOAP headers with the WCF adapters, see the SDK sample, Using Custom SOAP Headers with the WCF Adapters, from [https://go.microsoft.com/fwlink/?LinkId=79960](https://go.microsoft.com/fwlink/?LinkId=79960).

 The following example (from a Message Assignment or an Expression shape) shows the string setting the context property:

```
outboundMessageInstance(WCF.OutboundCustomHeaders) = "<headers><Origination>Home</Origination><Destination>Work</Destination></headers>"
```

## Creating an XmlDocument to set context properties
 You can set the **WCF.OutboundCustomHeaders** context property by creating an **XmlDocument** and writing the string value of the **XmlDocument** to the context property. You declare a variable of type **XMLDocument** and assign the XML data.

 The following example shows declaring a variable of type **XMLDocument** and assigning the XML data:

```
xmlDoc.LoadXml("<headers><Origination>Home</Origination><Destination>Work</Destination></headers>");
```

 The following example shows setting the context property:

```
RequestMessageInstance(WCF.OutboundCustomHeaders) = xmlDoc.OuterXml;
```

 For more information about using BizTalk Expression Editor, see [Requirements and Limitations for Expressions](../core/requirements-and-limitations-for-expressions.md). For more information about calling [!INCLUDE[btsDotNet](../includes/btsdotnet-md.md)] classes, see [Constructing Messages in User Code](../core/constructing-messages-in-user-code.md).

## See Also
 [WCF Adapters Property Schema and Properties](../core/wcf-adapters-property-schema-and-properties.md)
 [SOAP Headers with Consumed WCF Services](../core/soap-headers-with-consumed-wcf-services.md)
 [SOAP Headers with Published WCF Services](../core/soap-headers-with-published-wcf-services.md)
