---
description: "Learn more about: Accessing SOAP Headers in Orchestrations"
title: "Accessing SOAP Headers in Orchestrations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SOAP headers, orchestrations"
  - "SOAP headers, properties"
  - "orchestrations, SOAP headers"
ms.assetid: 91fe053a-3f16-497c-b4bb-5fb54bec62e5
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Accessing SOAP Headers in Orchestrations
You can access the SOAP header context properties in orchestrations for defined and unknown SOAP headers. For more information about property schemas and context properties, see [Property Schemas](../core/property-schemas.md).  
  
## Defined SOAP header context properties  
 The defined SOAP header context properties in orchestrations require a property schema. The property schema must have the target namespace `http://schemas.microsoft.com/BizTalk/2003/SOAPHeader`, and the **Property Schema Base** property set to **MessageContextPropertyBase**. Each root element name in the property schema must match the root element name of the defined SOAP header. You can then access the values of the context properties using the namespace of the property schema and the property name. The namespace of the property schema is different from the target namespace listed above. Although the namespace of the property schema can be any string, it usually defaults to the name of the project.  
  
 The following example shows accessing the SOAP header context property for a property schema namespace, **SOAPHeader**, and the property name **OrigDest**:  
  
```  
stringVar = requestMessageInstance(SOAPHeader.OrigDest);  
```  
  
> [!NOTE]
>  Defined SOAP headers are treated either as "in" or "out" headers. If the wizard defines the same SOAP header for the request and response message, the wizard does not automatically return the incoming value in the response. You must explicity copy the SOAP header context property of the request message to the SOAP header context property of the response message.  
  
## Copying SOAP header context property of incoming message  
 You can copy the SOAP header context property of an incoming message to the same SOAP header context property of the response message.  
  
 The following example shows copying the SOAP header context property:  
  
```  
ResponseMessageInstance(SOAPHeader.OrigDest) = RequestMessageInstance(SOAPHeader.OrigDest);  
```  
  
 When you create SOAP headers for the SOAP response, you ensure that you create your SOAP headers correctly. The SOAP adapter does not verify the contents of the SOAP header context properties. If the values of the response SOAP headers are incorrect, the SOAP adapter cannot send the response message to the consumer of your Web service.  
  
## Unknown SOAP header context property  
 The unknown SOAP header context property does not require a property schema. You can access this global context property **SOAP.UnknownHeaders**.  
  
 The following example shows accessing the unknown SOAP header context property **SOAP.UnknownHeaders**:  
  
```  
stringVar = RequestMessageInstance(SOAP.UnknownHeaders);  
```  
  
 The values contained in the context properties are strings containing XML data. The simplest way to access this data is to use the BizTalk Expression Editor in a **Message Assignment** or **Expression** shape and load the string in an **XmlDocument** and use XPATH queries to access specific fields. For more information creating XML documents in the BizTalk Expression Editor, see [XLANG-s Language](../core/xlang-s-language.md).  
  
 Context properties are associated with a particular message. The Messaging Engine does not automatically map the values of known SOAP headers from the request message to the response message. When creating the response message for a Web service, you must specifically set the SOAP header values. The following command is the simplest method of setting a SOAP header context property:  
  
```  
ResponseMessageInstance(SOAPHeader.OrigDest) = "<?xml version="1.0" encoding="utf-16"?><OrigDest xmlns=\"http://SOAPHeaderSchemas.OrigDestSOAPHeader\"><Origination xmlns=\"\">Home</Origination><Destination xmlns=\"\">Work</Destination> </OrigDest>"  
```  
  
 You can also achieve this by creating an **XmlDocument** and writing the string value of the **XmlDocument** to the context property.  
  
> [!NOTE]
>  If the **SOAP.UnknownHeaders** property is null, BizTalk automatically returns the unknown headers received in the SOAP request to the SOAP response. If the **SOAP.UnknownHeaders** context property on the response message is not null, then BizTalk returns that value to the SOAP response.  
  
## See Also  
 [SOAP Headers with Published Web Services](../core/soap-headers-with-published-web-services.md)
