---
title: "Create the receive location and send port programmatically | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 47850e66-ce33-4c6a-8190-168071792c0b
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Create the receive location and send port programmatically
Configure a WCF-BasicHttp receive location and send port programmatically. To use the BizTalk Administration console, see [WCF-BasicHttp adapter](../core/wcf-basichttp-adapter.md). 
  
## Configure the receive location programmatically  
  
 The BizTalk Explorer Object Model enables you to create and configure receive locations programmatically. The BizTalk Explorer Object Model exposes the**IReceiveLocation** receive location configuration interface that has a **TransportTypeData** read/write property. This property accepts a WCF-BasicHttp receive location configuration property bag in the form of a name-value pair of XML strings. To set this property in the BizTalk Explorer object model, you must set the **InboundTransportLocation** property of the **IReceiveLocation** interface.  
  
 The **TransportTypeData** property of the **IReceiveLocation** interface does not have to be set. If it is not set, the WCF-BasicHttp adapter uses the default values for the WCF-BasicHttp receive location configuration as indicated in the following table.  
 
 The following code fragment illustrates creating a WCF-BasicHttp receive location using the BizTalk Explorer Object Model:  
  
```  
// Use BizTalk Explorer object model to create new WCF-BasicHttp receive location   
string server = System.Environment.MachineName;  
string database = "BizTalkMgmtDb";  
string connectionString = string.Format("Server={0};Database={1};Integrated Security=true", server, database);  
string transportConfigData = @"<CustomProps>  
  <InboundBodyLocation vt=""8"">UseBodyElement</InboundBodyLocation>  
  <UseSSO vt=""11"">0</UseSSO>  
  <Identity vt=""8"">  
    <identity>  
    <userPrincipalName value=""username@contoso.com"" />  
    </identity>  
  </Identity>  
</CustomProps>";  
//requires project reference to \Program Files\Microsoft BizTalk Server 2009\Developer Tools\Microsoft.BizTalk.ExplorerOM.dll  
BtsCatalogExplorer explorer = new Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer();  
explorer.ConnectionString = connectionString;  
// Add a new BizTalk application  
Application application = explorer.AddNewApplication();  
application.Name = "SampleBizTalkApplication";  
// Save  
explorer.SaveChanges();  
// Add a new one-way receive port  
IReceivePort receivePort = application.AddNewReceivePort(false);  
receivePort.Name = "SampleReceivePort";  
// Add a new one-way receive location  
IReceiveLocation recieveLocation = receivePort.AddNewReceiveLocation();  
recieveLocation.Name = "SampleReceiveLocation";  
// Find a receive handler for WCF-BasicHttp  
int i = 0;  
for(i=0; i < explorer.ReceiveHandlers.Count; ++i)   
{  
    if("WCF-BasicHttp" == explorer.ReceiveHandlers[i].TransportType.Name)  
        break;  
}  
recieveLocation.ReceiveHandler = explorer.ReceiveHandlers[i];  
recieveLocation.Address = "/samplepath/sampleservice.svc";  
recieveLocation.ReceivePipeline = explorer.Pipelines["Microsoft.BizTalk.DefaultPipelines.PassThruReceive"];  
recieveLocation.TransportType = explorer.ProtocolTypes["WCF-BasicHttp"];  
recieveLocation.TransportTypeData = transportConfigData;  
// Save  
explorer.SaveChanges();  
  
```  

You can use the following format to set the properties in `<CustomProps>`: 
  
```  
<CustomProps>  
  <ServiceCertificate vt="8" />  
  <InboundBodyLocation vt="8">UseBodyElement</InboundBodyLocation>  
  <UseSSO vt="11">0</UseSSO>  
  <MessageClientCredentialType vt="8">UserName</MessageClientCredentialType>  
  <InboundBodyPathExpression vt="8" />  
  <SendTimeout vt="8">00:01:00</SendTimeout>  
  <OutboundXmlTemplate vt="8"><bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="xml"/></OutboundXmlTemplate>  
  <OpenTimeout vt="8">00:01:00</OpenTimeout>  
  <Identity vt="8">  
    <identity>  
    <userPrincipalName value="username@contoso.com" />  
    </identity>  
  </Identity>  
  <AlgorithmSuite vt="8">Basic256</AlgorithmSuite>  
  <SecurityMode vt="8">None</SecurityMode>  
  <TransportClientCredentialType vt="8">None</TransportClientCredentialType>  
  <MaxReceivedMessageSize vt="3">2097152</MaxReceivedMessageSize>  
  <TextEncoding vt="8">utf-8</TextEncoding>  
  <CloseTimeout vt="8">00:01:00</CloseTimeout>  
  <SuspendMessageOnFailure vt="11">0</SuspendMessageOnFailure>  
  <InboundNodeEncoding vt="8">Xml</InboundNodeEncoding>  
  <IncludeExceptionDetailInFaults vt="11">0</IncludeExceptionDetailInFaults>  
  <MaxConcurrentCalls vt="3">16</MaxConcurrentCalls>  
  <MessageEncoding vt="8">Text</MessageEncoding>  
  <OutboundBodyLocation vt="8">UseBodyElement</OutboundBodyLocation>  
</CustomProps>  
  
```   
  
The following table lists the configuration properties that you can set for the receive location:  
  
|Property name|Type|Description|  
|-------------------|----------|-----------------|  
|**Identity**|XML Blob<br /><br /> Example:<br /><br /> &lt;identity&gt;<br /><br /> &lt;userPrincipalName value="username@contoso.com" /&gt;<br /><br /> &lt;/identity&gt;|Specify the identity of the service that this receive location provides. The values that can be specified for the **Identity** property differ according to the security configuration. These settings enable the client to authenticate this receive location. In the handshake process between the client and service, the Windows Communication Foundation (WCF) infrastructure will ensure that the identity of the expected service matches the values of this element.<br /><br /> The default is an empty string.|  
|**OpenTimeout**|**System.TimeSpan**|Specify a time span value that indicates the interval of time provided for a channel open operation to complete.<br /><br /> Default value: 00:01:00|  
|**SendTimeout**|**System.TimeSpan**|Specify a time span value that indicates the interval of time provided for a send operation to complete. If you use a request-response receive port, this value specifies a time span for the whole interaction to complete, even if the client returns a large message.<br /><br /> Default value: 00:01:00|  
|**CloseTimeout**|**System.TimeSpan**|Specify a time span value that indicates the interval of time provided for a channel close operation to complete.<br /><br /> Default value: 00:01:00|  
|**MaxReceivedMessageSize**|Integer|Specify the maximum size, in bytes, for a message (including headers) that can be received on the wire. The size of the messages is bounded by the amount of memory allocated for each message. You can use this property to limit exposure to denial of service (DoS) attacks.<br /><br /> The WCF-BasicHttp adapter leverages the [BasicHttpBinding](http://go.microsoft.com/fwlink/?LinkId=81086) class in the buffered transfer mode to communicate with an endpoint. For the buffered transport mode, the [BasicHttpBinding.MaxBufferSize](http://go.microsoft.com/fwlink/?LinkId=80659) property is always equal to the value of this property.<br /><br /> Default value: 65536|  
|**MessageEncoding**|Enum<br /><br /> -   **Text** - Use a text message encoder.<br />-   **Mtom** - Use a Message Transmission Optimization Mechanism 1.0 (MTOM) encoder.|Specify the encoder used to encode the SOAP message.<br /><br /> Default value: **Text**|  
|**TextEncoding**|Enum<br /><br /> -   **unicodeFFF** - Unicode BigEndian encoding.<br />-   **utf-16** - 16-bit encoding.<br />-   **utf-8** - 8-bit encoding|Specify the character set encoding to be used for emitting messages on the binding when the **MessageEncoding** property is set to **Text**.<br /><br /> Default value: **utf-8**|  
|**MaxConcurrentCalls**|Integer|Specify the number of concurrent calls to a single service instance. Calls in excess of the limit are queued. The range of this property is from 1 to **Int32.MaxValue**.<br /><br /> Default value: 200|  
|**SecurityMode**|Enum<br /><br /> -   **None**<br />-   **Message**<br />-   **Transport**<br />-   **TransportWithMessageCredential**<br />-   **TransportCredentialOnly**<br /><br /> For more information about the member names for the **SecurityMode** property, see the **Security mode** property in the **WCF-BasicHttp Transport Properties Dialog Box, Receive, Security** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Specify the type of security that is used.<br /><br /> Default value: **None**|  
|**TransportClientCredentialType**|For more information about the member names for the **TransportClientCredentialType** property, see the **Transport client credential type** property in **WCF-BasicHttp Transport Properties Dialog Box, Receive, Security** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Specify the type of credential to be used when performing the client authentication.<br /><br /> Default value: **None**|  
|**MessageClientCredentialType**|Enum<br /><br /> -   **UserName**<br />-   **Certificate**<br /><br /> For more information about the member names for the **MessageClientCredentialType** property, see the **Message client credential type** property in **WCF-BasicHttp Transport Properties Dialog Box, Receive, Security** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Specify the type of credential to be used when performing client authentication using message-based security.<br /><br /> Default value: **UserName**|  
|**AlgorithmSuite**|Enum<br /><br /> For more information about the member names for the **AlgorithmSuite** property, see the **Algorithm suite** property in **WCF-BasicHttp Transport Properties Dialog Box, Receive, Security** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Specify the message encryption and key-wrap algorithms. These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.<br /><br /> Default value: **Basic256**|  
|**ServiceCertificate**|String|Specify the thumbprint of the X.509 certificate for this receive location that the clients use to authenticate the service. The certificate to be used for this property must be installed into the **My** store in the **Current User** location. **Note:**  You must install the service certificate into the **Current User** location of the user account for the receive handler hosting this receive location. <br /><br /> The default is an empty string.|  
|**UseSSO**|Boolean|Specify whether to use Enterprise Single Sign-On (SSO) to retrieve client credentials to issue an SSO ticket. For more information about the security configurations supporting SSO, see the section, "Enterprise Single Sign-On Supportability for the WCF-BasicHttp Receive Adapter" in **WCF-BasicHttp Transport Properties Dialog Box, Receive, Security** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].<br /><br /> Default value: **False**|  
|**InboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** - Use the content of the SOAP **Body** element of an incoming message to create the BizTalk message body part. If the **Body** element has more than one child element, only the first element becomes the BizTalk message body part.<br />-   **UseEnvelope** - Create the BizTalk message body part from the entire SOAP **Envelope** of an incoming message.<br />-   **UseBodyPath** - Use the body path expression in the **InboundBodyPathExpression** property to create the BizTalk message body part. The body path expression is evaluated against the immediate child element of the SOAP **Body** element of an incoming message. This property is valid only for solicit-response ports.<br /><br /> For more information about how to use the **InboundBodyLocation** property, see [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Specify the data selection for the SOAP **Body** element of incoming WCF messages.<br /><br /> Default value: **UseBodyElement**|  
|**InboundBodyPathExpression**|String<br /><br /> For more information about how to use the **InboundBodyPathExpression** property, see [WCF Adapters Property Schema and Properties](../core/wcf-adapters-property-schema-and-properties.md).|Specify the body path expression to identify a specific part of an incoming message used to create the BizTalk message body part. This body path expression is evaluated against the immediate child element of the SOAP **Body** node of an incoming message. If this body path expression returns more than one node, only the first node is chosen for the BizTalk message body part. This property is required if the **InboundBodyLocation** property is set to **UseBodyPath**.<br /><br /> The default is an empty string.|  
|**InboundNodeEncoding**|Enum<br /><br /> -   **Base64** - Base64 encoding.<br />-   **Hex** - Hexadecimal encoding.<br />-   **String** - Text encoding - UTF-8<br />-   **XML** - The WCF adapters create the BizTalk message body with the outer XML of the node selected by the body path expression in **InboundBodyPathExpression**.|Specify the type of encoding that the WCF-BasicHttp receive adapter uses to decode the node identified by the body path expression specified in **InboundBodyPathExpression**. This property is required if the **InboundBodyLocation** property is set to **UseBodyPath**.<br /><br /> Default value: **XML**|  
|**OutboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** - Use the BizTalk message body part to create the content of the SOAP **Body** element for an outgoing response message.<br />-   **UseTemplate** - Use the template supplied in the **OutboundXMLTemplate** property to create the content of the SOAP **Body** element for an outgoing response message.<br /><br /> For more information about how to use the **OutboundBodyLocation** property, see [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Specify the data selection for the SOAP **Body** element of outgoing WCF messages. This property is valid only for request-response receive locations.<br /><br /> Default value: **UseBodyElement**|  
|**OutboundXMLTemplate**|String<br /><br /> For more information about how to use the **OutboundXMLTemplate** property, see [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Specify the XML-formatted template for the content of the SOAP **Body** element of an outgoing response message. This property is required if the **OutboundBodyLocation** property is set to **UseTemplate**. This property is valid only for request-response receive locations.<br /><br /> The default is an empty string.|  
|**SuspendMessageOnFailure**|Boolean|Specify whether to suspend the request message that fails inbound processing due to a receive pipeline failure or a routing failure.<br /><br /> Default value: **False**|  
|**IncludeExceptionDetailInFaults**|Boolean|Specify whether to include managed exception information in the detail of SOAP faults returned to the client for debugging purposes.<br /><br /> Default: **False**|  
  
## Configure the send port programmatically   

 The following code fragment illustrates creating a WCF-BasicHttp send port using the BizTalk Explorer Object Model:    
  
```  
// Use BizTalk Explorer object model to create new WCF-BasicHttp send port.  
string server = System.Environment.MachineName;  
string database = "BizTalkMgmtDb";  
string connectionString = string.Format("Server={0};Database={1};Integrated Security=true", server, database);  
string transportConfigData = @"<CustomProps>  
                                 <StaticAction vt=""8"">http://www.northwindtraders.com/Service/Operation</StaticAction>  
                                 <MessageEncoding vt=""8"">Text</MessageEncoding>  
                                 <TextEncoding vt=""8"">utf-8</TextEncoding>  
                                 <OpenTimeout vt=""8"">00:01:00</OpenTimeout>  
                               </CustomProps>";  
//requires project reference to \Program Files\Microsoft BizTalk Server 2009\Developer Tools\Microsoft.BizTalk.ExplorerOM.dll  
BtsCatalogExplorer explorer = new Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer();  
explorer.ConnectionString = connectionString;  
// Add a new BizTalk application  
Application application = explorer.AddNewApplication();  
application.Name = "SampleBizTalkApplication";  
// Save  
explorer.SaveChanges();  
  
// Add a new static one-way send port  
SendPort sendPort = application.AddNewSendPort(false, false);   
sendPort.Name = "SampleSendPort";  
sendPort.PrimaryTransport.TransportType = explorer.ProtocolTypes["WCF-BasicHttp"];  
sendPort.PrimaryTransport.Address = "http://mycomputer/samplepath";  
sendPort.PrimaryTransport.TransportTypeData = transportConfigData; // propertyData; // need to change  
sendPort.SendPipeline = explorer.Pipelines["Microsoft.BizTalk.DefaultPipelines.PassThruTransmit"];  
// Save  
explorer.SaveChanges();  
```    

You can use the following format to set the properties in `<CustomProps>`: 
  
```  
<CustomProps>  
  <ServiceCertificate vt="8" />  
  <InboundBodyLocation vt="8">UseBodyElement</InboundBodyLocation>  
  <UseSSO vt="11">0</UseSSO>  
  <MessageClientCredentialType vt="8">UserName</MessageClientCredentialType>  
  <InboundBodyPathExpression vt="8" />  
  <SendTimeout vt="8">00:01:00</SendTimeout>  
  <OutboundXmlTemplate vt="8"><bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="xml"/></OutboundXmlTemplate>  
  <OpenTimeout vt="8">00:01:00</OpenTimeout>  
  <AlgorithmSuite vt="8">Basic256</AlgorithmSuite>  
  <SecurityMode vt="8">None</SecurityMode>  
  <TransportClientCredentialType vt="8">None</TransportClientCredentialType>  
  <ClientCertificate vt="8" />  
  <ProxyUserName vt="8" />  
  <MaxReceivedMessageSize vt="3">2097152</MaxReceivedMessageSize>  
  <TextEncoding vt="8">utf-8</TextEncoding>  
  <StaticAction vt="8">http://www.northwindtraders.com/Service/Operation</StaticAction>  
  <CloseTimeout vt="8">00:01:00</CloseTimeout>  
  <ProxyToUse vt="8">Default</ProxyToUse>  
  <InboundNodeEncoding vt="8">Xml</InboundNodeEncoding>  
  <PropagateFaultMessage vt="11">-1</PropagateFaultMessage>  
  <ProxyAddress vt="8" />  
  <MessageEncoding vt="8">Text</MessageEncoding>  
  <OutboundBodyLocation vt="8">UseBodyElement</OutboundBodyLocation>  
</CustomProps>  
  
```  

The following table lists the configuration properties that you can set for the send port:  
  
|Property name|Type|Description|  
|-------------------|----------|-----------------|  
|**SecurityMode**|Enum<br /><br /> -   **None**<br />-   **Message**<br />-   **Transport**<br />-   **TransportWithMessageCredential**<br />-   **TransportCredentialOnly**<br /><br /> For more information about the member names for the **SecurityMode** property, see the **Security mode** property in **WCF-BasicHttp Transport Properties Dialog Box, Send, Security** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Specify the type of security that is used.<br /><br /> Default value: **None**|  
|**MessageClientCredentialType**|Enum<br /><br /> -   **UserName**<br />-   **Certificate**<br /><br /> For more information about the member names for the **MessageClientCredentialType** property, see the **Message client credential type** property in **WCF-BasicHttp Transport Properties Dialog Box, Send, Security** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Specify the type of credential to be used when performing client authentication using message-based security.<br /><br /> Default value: **UserName**|  
|**TransportClientCredentialType**|Enum<br /><br /> -   **None**<br />-   **Basic**<br />-   **Windows**<br />-   **Certificate**<br />-   **Digest**<br />-   **Ntlm**<br /><br /> For more information about the member names for the **TransportClientCredentialType** property, see the **Transport client credential type** property in **WCF-BasicHttp Transport Properties Dialog Box, Send, Security** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Specify the type of credential to be used when performing the send port authentication.<br /><br /> Default value: **None**|  
|**UserName**|String|Specify the user name to use for authentication with the destination server when the **UseSSO** property is set to **False**. You do not have to use the domain\user format for this property.<br /><br /> The default is an empty string.|  
|**Password**|String|Specify the password to use for authentication with the destination server when the **UseSSO** property is set to **False**.<br /><br /> The default is an empty string.|  
|**AffiliateApplicationName**|String|Specify the affiliate application to use for Enterprise Single Sign-On (SSO).<br /><br /> The default is an empty string.|  
|**UseSSO**|Boolean|Specify whether to use Single Sign-On to retrieve client credentials for authentication with the destination server.<br /><br /> Default value: **False**|  
|**ClientCertificate**|String|Specify the thumbprint of the X.509 certificate for authenticating this send port to services. This property is required if the **ClientCredentialsType** property is set to **Certificate**. The certificate to be used for this property must be installed into the **My** store in the **Current User** location.<br /><br /> The default is an empty string.|  
|**ServiceCertificate**|String|Specify the thumbprint of the X.509 certificate for authenticating the service to which this send port sends messages. The certificate to be used for this property must be installed into the **Other People** store in the **Local Machine** location.<br /><br /> The default is an empty string.|  
|**ProxyToUse**|Enum<br /><br /> -   **None** - Do not use a proxy server for this send port.<br />-   **Default** - Use the proxy settings in the send handler hosting this send port.<br />-   **UserSpecified** - Use the proxy server specified in the **ProxyAddress** property|Specify which proxy server to use for outgoing HTTP traffic.<br /><br /> Default value: **None**|  
|**ProxyAddress**|String|Specify the address of the proxy server. Use the **https** or the **http** scheme depending on the security configuration. This address can be followed by a colon and the port number. For example, http://127.0.0.1:8080.<br /><br /> The default is an empty string.|  
|**ProxyUserName**|String|Specify the user name to use for the proxy. The WCF-BasicHttp adapter leverages the [BasicHttpBinding](http://go.microsoft.com/fwlink/?LinkId=81086) in the buffered transfer mode to communicate with an endpoint. Proxy credentials of **BasicHttpBinding** are applicable only when the security mode is **Transport**, **None**, or **TransportCredentialOnly**. If you set the **SecurityMode** property to **Message** or **TransportWithMessageCredential**, the WCF-BasicHttp adapter does not use the credential specified in the **ProxyUserName** and **ProxyPassword** properties for authentication against the proxy. **Note:**  The WCF-BasicHttp send adapter uses Basic authentication for the proxy.. <br /><br /> The default is an empty string.|  
|**ProxyPassword**|String|Specify the password to use for the proxy.<br /><br /> The default is an empty string.|  
|**InboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** - Use the content of the SOAP **Body** element of an incoming message to create the BizTalk message body part. If the **Body** element has more than one child element, only the first element becomes the BizTalk message body part. This property is valid only for solicit-response ports.<br />-   **UseEnvelope** - Create the BizTalk message body part from the entire SOAP **Envelope** of an incoming message.<br />-   **UseBodyPath** - Use the body path expression in the **InboundBodyPathExpression** property to create the BizTalk message body part. The body path expression is evaluated against the immediate child element of the SOAP **Body** element of an incoming message. This property is valid only for solicit-response ports.<br /><br /> For more information about how to use the **InboundBodyLocation** property, see [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Specify the data selection for the SOAP **Body** element of incoming WCF messages.<br /><br /> Default value: **UseBodyElement**|  
|**OutboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** - Use the BizTalk message body part to create the content of the SOAP **Body** element for an outgoing message.<br />-   **UseTemplate** - Use the template supplied in the **OutboundXMLTemplate** property to create the content of the SOAP **Body** element for an outgoing message.<br /><br /> For more information about how to use the **OutboundBodyLocation** property, see [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Specify the data selection for the SOAP **Body** element of outgoing WCF messages.<br /><br /> Default value: **UseBodyElement**|  
|**InboundBodyPathExpression**|String<br /><br /> For more information about how to use the **InboundBodyPathExpression** property, see [WCF Adapters Property Schema and Properties](../core/wcf-adapters-property-schema-and-properties.md).|Specify the body path expression to identify a specific part of an incoming message used to create the BizTalk message body part. This body path expression is evaluated against the immediate child element of the SOAP **Body** node of an incoming message. If this body path expression returns more than one node, only the first node is chosen for the BizTalk message body part. This property is required if the **InboundBodyLocation** property is set to **UseBodyPath**. This property is valid only for solicit-response ports.<br /><br /> The default is an empty string.|  
|**OutboundXMLTemplate**|String<br /><br /> For more information about how to use the **OutboundXMLTemplate** property, see [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Specify the XML-formatted template for the content of the SOAP **Body** element of an outgoing message. This property is required if the **OutboundBodyLocation** property is set to **UseTemplate**.<br /><br /> The default is an empty string.|  
|**InboundNodeEncoding**|Enum<br /><br /> -   **Base64** - Base64 encoding.<br />-   **Hex** - Hexadecimal encoding.<br />-   **String** - Text encoding - UTF-8<br />-   **XML** - The WCF adapters create the BizTalk message body with the outer XML of the node selected by the body path expression in **InboundBodyPathExpression**.|Specify the type of encoding that the WCF-BasicHttp send adapter uses to decode the node identified by the body path expression specified in **InboundBodyPathExpression**. This property is required if the **InboundBodyLocation** property is set to **UseBodyPath**. This property is valid only for solicit-response ports.<br /><br /> Default value: **XML**|  
|**StaticAction**|String|Specify the **SOAPAction** HTTP header field for outgoing messages. This property can also be set through the message context property **WCF.Action** in a pipeline or orchestration. You can specify this value in two different ways: the single action format and the action mapping format. If you set this property in the single action format—for example, http://contoso.com/Svc/Op1—the **SOAPAction** header for outgoing messages is always set to the value specified in this property.<br /><br /> If you set this property in the action mapping format, the outgoing **SOAPAction** header is determined by the **BTS.Operation** context property. For example, if this property is set to the following XML format and the **BTS.Operation** property is set to Op1, the WCF send adapter uses http://contoso.com/Svc/Op1 for the outgoing **SOAPAction** header.<br /><br /> \<BtsActionMapping\><br /><br /> \<Operation Name="Op1" Action="http://contoso.com/Svc/Op1" /\><br /><br /> \<Operation Name="Op2" Action="http://contoso.com/Svc/Op2" /\><br /><br /> \</BtsActionMapping\><br /><br /> If outgoing messages come from an orchestration port, orchestration instances dynamically set the **BTS.Operation** property with the operation name of the port. If outgoing messages are routed with content-based routing, you can set the **BTS.Operation** property in pipeline components.<br /><br /> The default is an empty string.|  
|**MaxReceivedMessageSize**|Integer|Specify the maximum size, in bytes, for a message (including headers) that can be received on the wire. The size of the messages is bounded by the amount of memory allocated for each message. You can use this property to limit exposure to denial of service (DoS) attacks.<br /><br /> The WCF-BasicHttp adapter leverages the [BasicHttpBinding](http://go.microsoft.com/fwlink/?LinkId=81086) class in the buffered transfer mode to communicate with an endpoint. For the buffered transport mode, the [BasicHttpBinding.MaxBufferSize](http://go.microsoft.com/fwlink/?LinkId=80659) property is always equal to the value of this property.<br /><br /> Default value: 65,536|  
|**MessageEncoding**|Enum<br /><br /> -   **Text** - Use a text message encoder.<br />-   **Mtom** - Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.|Specify the encoder used to encode the SOAP message.<br /><br /> Default value: **Text**|  
|**TextEncoding**|Enum<br /><br /> -   **unicodeFFF** - Unicode BigEndian encoding.<br />-   **utf-16** - 16-bit encoding.<br />-   **utf-8** - 8-bit encoding|Specify the character set encoding to be used for emitting messages on the binding when the **MessageEncoding** property is set to **Text**.<br /><br /> Default value: **utf-8**|  
|**SendTimeout**|**System.TimeSpan**|Specify a time span value that indicates the interval of time provided for a send operation to complete. If you use a solicit-response send port, this value specifies a time span for the whole interaction to complete, even if the service returns a large message.<br /><br /> Default value: 00:01:00|  
|**OpenTimeout**|**System.TimeSpan**|Specify a time span value that indicates the interval of time provided for a channel open operation to complete.<br /><br /> Default value: 00:01:00|  
|**CloseTimeout**|**System.TimeSpan**|Specify a time span value that indicates the interval of time provided for a channel close operation to complete.<br /><br /> Default value: 00:01:00|  
|**AlgorithmSuite**|Enum<br /><br /> For more information about the member names for the **AlgorithmSuite** property, see the **Algorithm suite** property in **WCF-BasicHttp Transport Properties Dialog Box, Send, Security** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Specify the message encryption and key-wrap algorithms. These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.<br /><br /> Default value : **Basic256**|  
|**Identity**|XML Blob<br /><br /> Example :<br /><br /> &lt;identity&gt;<br /><br /> &lt;userPrincipalName value="username@contoso.com" /&gt;<br /><br /> &lt;/identity&gt;|Specify the identity of the service that this send port expects. These settings enable this send port to authenticate the service. In the handshake process between the client and service, the Windows Communication Foundation (WCF) infrastructure will ensure that the identity of the expected service matches the values of this element.<br /><br /> The default is an empty string.|  
|**PropagateFaultMessage**|Boolean<br /><br /> -   **True** - Route the message that fails outbound processing to a subscribing application (such as another receive port or orchestration schedule).<br />-   **False** - Suspend failed messages and generate a negative acknowledgment (NACK).|Specify whether to route or suspend messages failed in outbound processing.<br /><br /> This property is valid only for solicit-response ports.<br /><br /> Default value : **True**|  
  
## See Also  
 [What Are the WCF Adapters?](../core/what-are-the-wcf-adapters.md)  
 [Publishing WCF Services with the Isolated WCF Receive Adapters](../core/publishing-wcf-services-with-the-isolated-wcf-receive-adapters.md)   
 [Configuring IIS for the Isolated WCF Receive Adapters](../core/configuring-iis-for-the-isolated-wcf-receive-adapters.md)   
 [Managing BizTalk Hosts and Host Instances](../core/managing-biztalk-hosts-and-host-instances.md)   
 [How to Change Service Accounts and Passwords](../core/how-to-change-service-accounts-and-passwords.md)   
 [Installing Certificates for the WCF Adapters](../core/installing-certificates-for-the-wcf-adapters.md)   
 [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md)    
  [WCF Adapters Property Schema and Properties](../core/wcf-adapters-property-schema-and-properties.md)   
 [Configuring Dynamic Send Ports Using WCF Adapters Context Properties](../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)