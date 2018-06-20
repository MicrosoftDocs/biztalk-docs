---
title: "SOAP Headers with Published WCF Services | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "publishing, SOAP headers [WCF services]"
  - "SOAP headers, WCF services"
  - "WCF services, SOAP headers"
ms.assetid: 5564a57e-e241-4595-a959-4289c8502410
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SOAP Headers with Published WCF Services
The WCF receive adapters can copy all the SOAP header values in the inbound messages to the **InboundHeaders** property, or they can write or promote specified values to the BizTalk message context. The adapters can work with both custom SOAP headers and standard SOAP headers that the WCF infrastructure uses, such as WS-Addressing, WS-Security, and WS-AtomicTransaction. The **InboundHeaders** context property is in the target namespace **http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties**, and contains string representations of the SOAP header values in inbound messages.  
  
> [!NOTE]
>  If you are going to promote the SOAP header values you specified, there must be a deployed property schema in your BizTalk project that corresponds to the values you are promoting.  
  
> [!NOTE]
>  The promoted properties cannot be longer than 256 characters.  
  
 The following XML data shows an example of the string representation of the SOAP headers for the **InboundHeaders** property. This comes from the client and is sent to the BizTalk receive location.  
  
```  
<headers>  
<a:Action s:mustUnderstand="1" xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://www.w3.org/2005/08/addressing">Operation_1</a:Action>  
<SalesAgent xmlns="Microsoft.Samples.BizTalk.WCF.CustomSoapHeaderPipeline">Contoso</SalesAgent>  
<a:MessageID xmlns:a="http://www.w3.org/2005/08/addressing">urn:uuid:26e6720f-5a82-4ef2-b597-6ef077bab92e</a:MessageID>  
<a:ReplyTo xmlns:a="http://www.w3.org/2005/08/addressing"><a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address></a:ReplyTo>  
<a:To s:mustUnderstand="1" xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://www.w3.org/2005/08/addressing">net.tcp://localhost:9990/NetTcpOrderProcess</a:To>  
</headers>  
```  
  
 To write or promote SOAP header values to the BizTalk message context, you need to put a collection of value pairs that consist of property name and namespace into the WCF message so that the WCF adapters will recognize that the header values are to be written or promoted. A WCF adapter expects the following message properties in the WCF messages for writing or promoting SOAP header values to the BizTalk message context:  
  
- To promote the SOAP header values to the BizTalk message context, WCF adapters are looking for the pair of key **http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties/Promote** and value **List\<KeyValuePair\<XmlQualifiedName, object\>\>**.  
  
   Using this pair, WCF adapters take the namespace, name, and value from the **XmlQualifiedName** object and use them for promoting the header values.  
  
- To write but not promote the SOAP header values to the BizTalk message context, WCF adapters are looking for the pair of key **http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties/WriteToContext** and value **List\<KeyValuePair\<XmlQualifiedName, object\>\>**.  
  
   Using this pair, WCF adapters write the values to the message context.  
  
  The following code shows how to write or promote the SOAP header values to the BizTalk message context:  
  
```  
const string PropertiesToPromoteKey="http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties/Promote";  
const string PropertiesToWriteKey="http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties/WriteToContext";  
  
XmlQualifiedName PropName1=new XmlQualifiedName("Destination", "http://tempuri.org/2007/sample-properties");  
XmlQualifiedName PropName2=new XmlQualifiedName("Source", "http://tempuri.org/2007/sample-properties");  
  
//Create a List of KeyValuePairs that indicate properties to be promoted to BizTalk message context.   
//A Property Schema must be deployed and string values have a limit of 256 characters  
List<KeyValuePair<XmlQualifiedName, object>> promoteProps=new List<KeyValuePair<XmlQualifiedName, object>>();  
promoteProps.Add(new KeyValuePair<XmlQualifiedName, object>(PropName1, "Property value"));  
wcfMessage.Properties[PropertiesToPromoteKey]=promoteProps;  
  
//Create a List of KeyValuePairs that indicate properties to be written to BizTalk message context  
List<KeyValuePair<XmlQualifiedName, object>> writeProps=new List<KeyValuePair<XmlQualifiedName, object>>();  
writeProps.Add(new KeyValuePair<XmlQualifiedName, object>(PropName2, "Property value"));  
wcfMessage.Properties[PropertiesToWriteKey]=writeProps;  
```  
  
 The BizTalk WCF Service Publishing Wizard does not include custom SOAP header definitions in the generated metadata. To publish metadata for WCF services using custom SOAP headers, you should manually create a Web Services Description Language (WSDL) file. You can use the **externalMetadataLocation** attribute of the [\<serviceMetadata\>](http://go.microsoft.com/fwlink/?LinkId=89121) element in the Web.config file that the wizard generates to specify the location of the WSDL file. The WSDL file is returned to the user in response to WSDL and metadata exchange (MEX) requests instead of the auto-generated WSDL.  
  
 The following XML data shows an example of a part of the WSDL file defining custom SOAP headers:  
  
```  
<wsdl:operation name="Request">  
  <soap12:operation soapAction="http://Microsoft.Samples.BizTalk.NetTcpAdapter/OrderProcess/IOrderProcess/Request" style="document" />   
   <wsdl:input name="Order">  
     <soap12:header message="i0:Order_Headers" part="SalesAgent" use="literal" />   
     <soap12:body use="literal" />   
   </wsdl:input>  
   <wsdl:output name="OrderConfirmation">  
     <soap12:header message="i0:OrderConfirmation_Headers" part="PaymentAgent" use="literal" />   
     <soap12:body use="literal" />   
   </wsdl:output>  
</wsdl:operation>  
```  
  
## In This Section  
  
-   [Accessing SOAP Headers in WCF Messages with Orchestrations](../core/accessing-soap-headers-in-wcf-messages-with-orchestrations.md)  
  
-   [Accessing SOAP Headers in WCF Messages with Pipeline Components](../core/accessing-soap-headers-in-wcf-messages-with-pipeline-components.md)  
  
## See Also  
 [WCF Adapters Property Schema and Properties](../core/wcf-adapters-property-schema-and-properties.md)   
 [SOAP Headers with Consumed WCF Services](../core/soap-headers-with-consumed-wcf-services.md)