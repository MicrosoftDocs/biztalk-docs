---
description: "Learn more about: Using SOAP Headers in Orchestrations"
title: "Using SOAP Headers in Orchestrations"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Using SOAP Headers in Orchestrations
Orchestrations use property schemas to define SOAP header context properties. You use the BizTalk Editor to set SOAP header context properties.  
  
## Defining SOAP header context properties with property schemas  
 You need a property schema to use defined SOAP header context properties in orchestrations. The property schema must have the target namespace of `http://schemas.microsoft.com/BizTalk/2003/SOAPHeader`, and the **Property Schema Base** property set to **MessageContextPropertyBase**. Each root element name in the property schema must match the root element name in the defined SOAP header. You can then set values for the context properties using the namespace of the property schema and the property name.  
  
> [!NOTE]
>  The namespace of the property schema is different from the namespace of the target schema (`http://schemas.microsoft.com/BizTalk/2003/SOAPHeader`). Your namespace can be any string; however, it usually defaults to the name of the project.  
  
 The following code shows assigning a SOAP header context property where the property schema namespace is **SOAPHeader** with a property name of **OrigDest**:  
  
```  
requestMessageInstance(SOAPHeader.OrigDest) = stringVar;  
```  
  
 For more information about property schemas and context properties, see [Property Schemas](../core/property-schemas.md).  
  
## Using BizTalk Editor to set SOAP header context properties  
 For orchestrations, the SOAP header context properties are set to strings that contain XML data. You set these strings using the BizTalk Expression Editor in a **Message Assignment** or **Expression** shape.  
  
 The following example shows the string setting the context property:  
  
```  
RequestMessageInstance(SOAPHeader.OrigDest) = "<?xml version=\"1.0\"?>  
<OrigDest xmlns=\"http://SOAPHeaderSchemas.OrigDestSOAPHeader\">  
<Origination>Home</Origination>  
<Destination>Work</Destination>  
</OrigDest>"  
```  
  
## Using BizTalk Editor to create an instance of a SOAP header root element  
 Setting the SOAP header to the correct string can be difficult. When adding a Web reference to a BizTalk project, all complex Web message parts are added to Reference.xsd as root elements. Reference.xsd also contains root elements for each defined SOAP header. To ensure that you set the SOAP header with the correct string, you should use BizTalk Editor to create an instance of the SOAP header root element for Reference.xsd. You can use the generated instance data directly or the instance data to contain your real data.  
  
 For more information about using the BizTalk Editor to generate instance data, see [How to Generate Instance Messages](../core/how-to-generate-instance-messages.md).  
  
## Creating an XmlDocument to set context properties  
 You can set context properties by creating an **XmlDocument** and writing the string value of the **XmlDocument** to the context property. You declare a variable of type **XMLDocument** and assign the XML data.  
  
 The following example shows setting a declaring a variable of type **XMLDocument** and assign the XML data:  
  
```  
xmlDoc.LoadXml("<?xml version=\"1.0\"?><OrigDest xmlns=\"http://SOAPHeaderSchemas.OrigDestSOAPHeader\"><Origination>Home</Origination><Destination>Work</Destination></OrigDest>");  
```  
  
 The following example shows setting the context property:  
  
```  
RequestMessageInstance(SOAPHeader.OrigDest) = xmlDoc.OuterXml;  
```  
  
 For more information about using BizTalk Expression Editor, see [Requirements and Limitations for Expressions](../core/requirements-and-limitations-for-expressions.md). For more information about calling .NET classes, see [Constructing Messages in User Code](../core/constructing-messages-in-user-code.md).  
  
## Creating SOAP headers for a SOAP request  
 When you create SOAP headers for the SOAP request, you must ensure that you have correctly created the SOAP headers. The SOAP adapter does not verify the contents of the SOAP header context properties.  
  
> [!NOTE]
>  If the SOAP header is incorrect, BizTalk cannot send the SOAP request to the Web service.  
  
 The SOAP response that BizTalk returns to the Web service may also contain SOAP headers. You can only access these SOAP headers if they are defined SOAP headers.  
  
> [!NOTE]
>  Consumed Web services support only defined SOAP headers.  
  
 For more information about defined SOAP headers, see [Using SOAP Headers](../core/using-soap-headers.md). The response SOAP headers are set to context properties using the same syntax as the request SOAP headers.  
  
 The following code shows how to access the response SOAP headers:  
  
```  
stringVar = ResponseMessageInstance(SOAPHeader.OrigDest);  
```  
  
 The values contained in the context properties are strings containing XML data. You set these strings using BizTalk Expression Editor in a **Message Assignment** or **Expression** shape. You load the string in an **XmlDocument** and use XPath queries to access specific fields.  
  
 For more information about creating XML documents in BizTalk Expression Editor, see [XLANG-s Language](../core/xlang-s-language.md).  
  
## See Also  
 [XLANG-s Language](../core/xlang-s-language.md)   
 [SOAP Headers with Consumed Web Services](../core/soap-headers-with-consumed-web-services.md)
