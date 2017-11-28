---
title: "How to Configure a WCF-WSHttp Send Port | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 035d9a62-b8a3-4705-a7bc-b62676437206
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure a WCF-WSHttp Send Port
You can configure a WCF-WSHttp send port either programmatically or by using the BizTalk Administration console.  
  
## Configuration properties
  
 The BizTalk Explorer Object Model exposes an adapter-specific interface for send ports named **ITransportInfo** that has the **TransportTypeData** read/write property. This property accepts a WCF-WSHttp send port configuration property bag in the form of a name-value pair of XML strings.  
  
 The **TransportTypeData** property of the **ITransportInfo** interface is not required. If it is not set, the adapter uses the default values for the WCF-WSHttp send port configuration, as indicated in the following table.  
  
 The following table lists the configuration properties you can set in the BizTalk Explorer Object Model for WCF-WSHttp send ports.  
  
|Property name|Type|Description|  
|-------------------|----------|-----------------|  
|**Identity**|XML Blob<br /><br /> Example :<br /><br /> &lt;identity&gt;<br /><br /> &lt;userPrincipalName value="username@contoso.com" /&gt;<br /><br /> &lt;/identity&gt;|Specify the identity of the service that this send port expects. These settings enable this send port to authenticate the service. In the handshake process between the client and service, the Windows Communication Foundation (WCF) infrastructure will ensure that the identity of the expected service matches the values of this element.<br /><br /> The default is an empty string.|  
|**StaticAction**|-   String|Specify the **SOAPAction** HTTP header field for outgoing messages. This property can also be set through the message context property **WCF.Action** in a pipeline or orchestration. You can specify this value in two different ways: the single action format and the action mapping format. If you set this property in the single action format- for example, http://contoso.com/Svc/Op1- the **SOAPAction** header for outgoing messages is always set to the value specified in this property.<br /><br /> If you set this property in the action mapping format, the outgoing **SOAPAction** header is determined by the **BTS.Operation** context property. For example, if this property is set to the following XML format and the **BTS.Operation** property is set to Op1, the WCF send adapter uses http://contoso.com/Svc/Op1 for the outgoing **SOAPAction** header.<br /><br /> \<BtsActionMapping\><br /><br /> \<Operation Name="Op1" Action="http://contoso.com/Svc/Op1" /\><br /><br /> \<Operation Name="Op2" Action="http://contoso.com/Svc/Op2" /\><br /><br /> \</BtsActionMapping\><br /><br /> If outgoing messages come from an orchestration port, orchestration instances dynamically set the **BTS.Operation** property with the operation name of the port. If outgoing messages are routed with content-based routing, you can set the **BTS.Operation** property in pipeline components.<br /><br /> The default is an empty string.|  
|**OpenTimeout**|**System.TimeSpan**|Specify a time span value that indicates the interval of time provided for a channel open operation to complete.<br /><br /> Default value: 00:01:00|  
|**SendTimeout**|**System.TimeSpan**|Specify a time span value that indicates the interval of time provided for a send operation to complete. If you use a solicit-response send port, this value specifies a time span for the whole interaction to complete, even if the service returns a large message.<br /><br /> Default value: 00:01:00|  
|**CloseTimeout**|**System.TimeSpan**|Specify a time span value that indicates the interval of time provided for a channel close operation to complete.<br /><br /> Default value: 00:01:00|  
|**MaxReceivedMessageSize**|Integer|Specify the maximum size, in bytes, for a message (including headers) that can be received on the wire. The size of the messages is bounded by the amount of memory allocated for each message. You can use this property to limit exposure to denial of service (DoS) attacks.<br /><br /> Default value: 65536|  
|**MessageEncoding**|Enum<br /><br /> -   **Text** - Use a text message encoder.<br />-   **Mtom** - Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.|Specify the encoder used to encode the SOAP message.<br /><br /> Default value: **Text**|  
|**TextEncoding**|Enum<br /><br /> -   **unicodeFFF** - Unicode BigEndian encoding.<br />-   **utf-16** - 16-bit encoding.<br />-   **utf-8** - 8-bit encoding.|Specify the character set encoding to be used for emitting messages on the binding when the **MessageEncoding** property is set to **Text**.<br /><br /> Default value: **utf-8**|  
|**EnableTransaction**|Boolean|Specify whether a message is transmitted to the destination service and deleted from the MessageBox database in a transactional context using the **WS-AtomicTransaction** protocol.<br /><br /> Default value: **False**|  
|**SecurityMode**|Enum<br /><br /> -   **None**<br />-   **Message**<br />-   **Transport**<br />-   **TransportWithMessageCredential**<br /><br /> For more information about the member names for the **SecurityMode** property, see the **Security mode** property in the **WCF-WSHttp Transport Properties Dialog Box, Send, Security** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Specify the type of security that is used.<br /><br /> Default value: **None**|  
|**TransportClientCredentialType**|Enum<br /><br /> -   **None**<br />-   **Basic**<br />-   **Windows**<br />-   **Certificate**<br />-   **Digest**<br />-   **Ntlm**<br /><br /> For more information about the member names for the **TransportClientCredentialType** property, see the **Transport client credential type** property in the **WCF-WSHttp Transport Properties Dialog Box, Send, Security** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Specify the type of credential to be used when performing the send port authentication.<br /><br /> Default value: **None**|  
|**MessageClientCredentialType**|Enum<br /><br /> -   **None**<br />-   **Windows**<br />-   **UserName**<br />-   **Certificate**<br /><br /> For more information about the member names for the **MessageClientCredentialType** property, see the **Message client credential type** property in the **WCF-WSHttp Transport Properties Dialog Box, Send, Security** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Specify the type of credential to be used when performing client authentication using message-based security.<br /><br /> Default value: **UserName**|  
|**AlgorithmSuite**|Enum<br /><br /> For more information about the member names for the **AlgorithmSuite** property, see the **Algorithm suite** property in the **WCF-WSHttp Transport Properties Dialog Box, Send, Security** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Specify the message encryption and key-wrap algorithms. These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.<br /><br /> Default value: **Basic256**|  
|**NegotiateServiceCredential**|Boolean<br /><br /> For more information about the member names for the **NegotiateServiceCredential** property, see the **Negotiate service credential** property in the **WCF-WSHttp Transport Properties Dialog Box, Send, Security** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Specify whether the service credential is provisioned at this send port out of band, or is obtained from the service to this send port through a process of negotiation. Such a negotiation is a precursor to the usual message exchange.<br /><br /> Default value: **False**|  
|**EnableSecurityContext**|Boolean|Specify whether a security context token is established through a **WS-SecureConversation** exchange between this send port and the service. If this property is set to **True** then the destination service must support **WS-SecureConversation**.<br /><br /> Default value: **True**|  
|**ClientCertificate**|String|Specify the thumbprint of the X.509 certificate for authenticating this send port to services. This property is required if the **ClientCredentialsType** property is set to **Certificate**. The certificate to be used for this property must be installed into the **My** store in the **Current User** location.<br /><br /> The default is an empty string.|  
|**ServiceCertificate**|String|Specify the thumbprint of the X.509 certificate for authenticating the service to which this send port sends messages. The certificate to be used for this property must be installed into the **Other People** store in the **Local Machine** location.<br /><br /> The default is an empty string.|  
|**AffiliateApplicationName**|String|Specify the affiliate application to use for Enterprise Single Sign-On (SSO).<br /><br /> The default is an empty string.|  
|**UseSSO**|Boolean|Specify whether to use Single Sign-On to retrieve client credentials for authentication with the destination server.<br /><br /> Default value: **False**|  
|**UserName**|String|Specify the user name to use for authentication with the destination server when the **UseSSO** property is set to **False**. You do not have to use the domain\user format for this property.<br /><br /> The default is an empty string.|  
|**Password**|String|Specify the password to use for authentication with the destination server when the **UseSSO** property is set to **False**.<br /><br /> The default is an empty string.|  
|**ProxyToUse**|Enum<br /><br /> -   **None** - Do not use a proxy server for this send port.<br />-   **Default** - Use the proxy settings in the send handler hosting this send port.<br />-   **UserSpecified** - Use the proxy server specified in the **ProxyAddress** property.|Specify which proxy server to use for outgoing HTTP traffic.<br /><br /> Default value: **None**|  
|**ProxyAddress**|String|Specify the address of the proxy server. Use the **https** or the **http** scheme depending on the security configuration. This address can be followed by a colon and the port number. For example, http://127.0.0.1:8080.<br /><br /> The default is an empty string.|  
|**ProxyUserName**|String|Specify the user name to use for the proxy. The WCF-WSHttp adapter leverages the [WSHttpBinding](http://go.microsoft.com/fwlink/?LinkId=81206) in the buffered transfer mode to communicate with an endpoint. Proxy credentials of **WSHttpBinding** are applicable only when the security mode is **Transport**, or **None**. If you set the **SecurityMode** property to **Message** or **TransportWithMessageCredential**, the WCF-WSHttp adapter does not use the credential specified in the **ProxyUserName** and **ProxyPassword** properties for authentication against the proxy. **Note:**  The WCF-WSHttp send adapter uses the basic authentication for the proxy. <br /><br /> The default is an empty string.|  
|**ProxyPassword**|String|Specify the password to use for the proxy.<br /><br /> The default is an empty string.|  
|**OutboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** - Use the BizTalk message body part to create the content of the SOAP **Body** element for an outgoing message.<br />-   **UseTemplate** - Use the template supplied in the **OutboundXMLTemplate** property to create the content of the SOAP **Body** element for an outgoing message.<br /><br /> For more information about how to use the **OutboundBodyLocation** property, see [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Specify the data selection for the SOAP **Body** element of outgoing WCF messages.<br /><br /> Default value: **UseBodyElement**|  
|**OutboundXMLTemplate**|String<br /><br /> For more information about how to use the **OutboundXMLTemplate** property, see [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Specify the XML-formatted template for the content of the SOAP **Body** element of an outgoing message. This property is required if the **OutboundBodyLocation** property is set to **UseTemplate**.<br /><br /> The default is an empty string.|  
|**InboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** - Use the content of the SOAP **Body** element of an incoming message to create the BizTalk message body part. If the **Body** element has more than one child element, only the first element becomes the BizTalk message body part. This property is valid only for solicit-response ports.<br />-   **UseEnvelope** - Create the BizTalk message body part from the entire SOAP **Envelope** of an incoming message.<br />-   **UseBodyPath** - Use the body path expression in the **InboundBodyPathExpression** property to create the BizTalk message body part. The body path expression is evaluated against the immediate child element of the SOAP **Body** element of an incoming message. This property is valid only for solicit-response ports.<br /><br /> For more information about how to use the **InboundBodyLocation** property, see [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Specify the data selection for the SOAP **Body** element of incoming WCF messages.<br /><br /> Default value: **UseBodyElement**|  
|**InboundBodyPathExpression**|String<br /><br /> For more information about how to use the **InboundBodyPathExpression** property, see [WCF Adapters Property Schema and Properties](../core/wcf-adapters-property-schema-and-properties.md).|Specify the body path expression to identify a specific part of an incoming message used to create the BizTalk message body part. This body path expression is evaluated against the immediate child element of the SOAP **Body** node of an incoming message. If this body path expression returns more than one node, only the first node is chosen for the BizTalk message body part. This property is required if the **InboundBodyLocation** property is set to **UseBodyPath**. This property is valid only for solicit-response ports.<br /><br /> The default is an empty string.|  
|**InboundNodeEncoding**|Enum<br /><br /> -   **Base64** - Base64 encoding.<br />-   **Hex** - Hexadecimal encoding.<br />-   **String** - Text encoding - UTF-8.<br />-   **XML** - The WCF adapters create the BizTalk message body with the outer XML of the node selected by the body path expression in **InboundBodyPathExpression**.|Specify the type of encoding that the WCF-WSHttp send adapter uses to decode for the node identified by the body path specified in **InboundBodyPathExpression**. This property is required if the **InboundBodyLocation** property is set to **UseBodyPath**. This property is valid only for solicit-response ports.<br /><br /> Default value: **XML**|  
|**PropagateFaultMessage**|Boolean<br /><br /> -   **True** - Route the message that fails outbound processing to a subscribing application (such as another receive port or orchestration schedule).<br />-   **False** - Suspend failed messages and generate a negative acknowledgment (NACK).|Specify whether to route or suspend messages failed in outbound processing.<br /><br /> This property is valid only for solicit-response ports.<br /><br /> Default value: **True**|  
  
## Configure a WCF-WSHttp Send Port with the BizTalk Administration Console
  
 You can set WCF-WSHttp send port adapter variables in the BizTalk Administration console. If properties are not set for the send port, the default values for the WCF-WSHttp send port configuration are used, as indicated in the previous table.  
  
## Configure variables for a WCF-WSHttp send port  
  
1.  In the BizTalk Administration console, create a new send port or double-click an existing send port to modify it. For more information, see [How to Create a Send Port](../core/how-to-create-a-send-port2.md). Configure all of the send port options and specify **WCF-WSHttp** for the **Type** option in the **Transport** section of the **General** tab.  
  
2.  On the **General** tab, in the **Transport** section, click the **Configure** button next to **Type**.  
  
3.  In the **WCF-WSHttp Transport Properties** dialog box, on the **General** tab, configure the endpoint address, the service identity, and the **SOAPAction** HTTP header for the WCF-WSHttp send port. For more information about the **General** tab in the **WCF-WSHttp Transport Properties** dialog box, see the **WCF-WSHttp Transport Properties Dialog Box, Send, General** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
4.  In the **WCF-WSHttp Transport Properties** dialog box, on the **Binding** tab, configure the time-out, encoding, and transaction properties. For more information about the **Binding** tab in the **WCF-WSHttp Transport Properties** dialog box, see the **WCF-WSHttp Transport Properties Dialog Box, Send, Binding** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
5.  In the **WCF-WSHttp Transport Properties** dialog box, on the **Security** tab, define the security capabilities of the WCF-WSHttp send port. For more information about the **Security** tab in the **WCF-WSHttp Transport Properties** dialog box, see the **WCF-WSHttp Transport Properties Dialog Box, Send, Security** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
6.  In the **WCF-WSHttp Transport Properties** dialog box, on the **Proxy** tab, configure the proxy setting for the WCF-WSHttp send port. For more information about the **Proxy** tab in the **WCF-WSHttp Transport Properties** dialog box, see the **WCF-WSHttp Transport Properties Dialog Box, Send, Proxy** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
7.  In the **WCF-WSHttp Transport Properties** dialog box, on the **Messages** tab, specify the data selection for the SOAP **Body** element. For more information about the **Messages** tab in the **WCF-WSHttp Transport Properties** dialog box, see the **WCF-WSHttp Transport Properties Dialog Box, Send, Messages** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## Configure a WCF-WSHttp Send Port Programmatically
  
 You can use the following format to set the properties:  

```  
 <CustomProps>    
  <ServiceCertificate vt="8" />  
  <UseSSO vt="11">0</UseSSO>  
  <InboundBodyPathExpression vt="8" />  
  <MessageClientCredentialType vt="8">Windows</MessageClientCredentialType>  
  <SendTimeout vt="8">00:01:00</SendTimeout>  
  <OutboundXmlTemplate vt="8"><bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="xml"/></OutboundXmlTemplate>  
  <OpenTimeout vt="8">00:01:00</OpenTimeout>  
  <Identity vt="8" />  
  <AlgorithmSuite vt="8">Basic256</AlgorithmSuite>  
  <SecurityMode vt="8">Message</SecurityMode>  
  <TransportClientCredentialType vt="8">Windows</TransportClientCredentialType>  
  <TextEncoding vt="8">utf-8</TextEncoding>  
  <NegotiateServiceCredential vt="11">-1</NegotiateServiceCredential>  
  <MaxReceivedMessageSize vt="3">2097152</MaxReceivedMessageSize>  
  <ClientCertificate vt="8" />  
  <ProxyUserName vt="8" />  
  <CloseTimeout vt="8">00:01:00</CloseTimeout>  
  <ProxyToUse vt="8">Default</ProxyToUse>  
  <EnableTransaction vt="11">0</EnableTransaction>  
  <InboundBodyLocation vt="8">UseBodyElement</InboundBodyLocation>  
  <InboundNodeEncoding vt="8">Xml</InboundNodeEncoding>  
  <EstablishSecurityContext vt="11">-1</EstablishSecurityContext>  
  <StaticAction vt="8">http://www.northwindtraders.com/Service/Operation</StaticAction>  
  <PropagateFaultMessage vt="11">-1</PropagateFaultMessage>  
  <ProxyAddress vt="8" />  
  <MessageEncoding vt="8">Text</MessageEncoding>  
  <OutboundBodyLocation vt="8">UseBodyElement</OutboundBodyLocation>  
</CustomProps>  
  
```  
  
 The following code fragment illustrates creating a WCF-WSHttp send port:  
  
```  
// Use BizTalk Explorer object model to create new WCF-WSHttp send port.  
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
sendPort.PrimaryTransport.TransportType = explorer.ProtocolTypes["WCF-WSHttp"];  
sendPort.PrimaryTransport.Address = "http://mycomputer/samplepath";  
sendPort.PrimaryTransport.TransportTypeData = transportConfigData; // propertyData; // need to change  
sendPort.SendPipeline = explorer.Pipelines["Microsoft.BizTalk.DefaultPipelines.PassThruTransmit"];  
// Save  
explorer.SaveChanges();  
```  
  
## See Also  
 [WCF Adapters Property Schema and Properties](../core/wcf-adapters-property-schema-and-properties.md)   
 [Configuring the WCF-WSHttp Adapter](../core/configuring-the-wcf-wshttp-adapter.md)   
 [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md)   
 [Installing Certificates for the WCF Adapters](../core/installing-certificates-for-the-wcf-adapters.md)   
 [Configuring Dynamic Send Ports Using WCF Adapters Context Properties](../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)