---
title: "How to Configure a WCF-Custom Send Port | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a195c047-5d5c-478b-accd-252e9dc5cfe8
caps.latest.revision: 19
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure a WCF-Custom Send Port
You can configure a WCF-Custom send port either programmatically or by using the BizTalk Administration console.  
  
## Configuration properties
  
 The BizTalk Explorer Object Model exposes an adapter-specific interface for send ports named **ITransportInfo** that has the **TransportTypeData** read/write property. This property accepts a WCF-Custom send port configuration property bag in the form of a name-value pair of XML strings.  
  
 The **TransportTypeData** property of the **ITransportInfo** interface is not required. If it is not set, the adapter uses the default values for the WCF-Custom send port configuration, as indicated in the following table.  
  
 The following table lists the configuration properties you can set in the BizTalk Explorer Object Model for WCF-Custom send ports.  
  
|Property name|Type|Description|  
|-------------------|----------|-----------------|  
|**Identity**|XML Blob<br /><br /> Example:<br /><br /> &lt;identity&gt;<br /><br /> &lt;userPrincipalName value="username@contoso.com" /&gt;<br /><br /> &lt;/identity&gt;|Specify the identity of the service that this send port expects. These settings enable this send port to authenticate the service. In the handshake process between the client and service, the WCF infrastructure will ensure that the identity of the expected service matches the values of this element. The values that can be specified for the **Identity** property differ according to the security configuration.<br /><br /> The default is an empty string.|  
|**StaticAction**|String|Specify the **SOAPAction** header field for outgoing messages. This property can also be set through the message context property **WCF.Action** in a pipeline or orchestration. You can specify this value in two different ways: the single action format and the action mapping format. If you set this property in the single action format- for example, http://contoso.com/Svc/Op1- the **SOAPAction** header for outgoing messages is always set to the value specified in this property.<br /><br /> If you set this property in the action mapping format, the outgoing **SOAPAction** header is determined by the **BTS.Operation** context property. For example, if this property is set to the following XML format and the **BTS.Operation** property is set to Op1, the WCF send adapter uses http://contoso.com/Svc/Op1 for the outgoing **SOAPAction** header.<br /><br /> \<BtsActionMapping\><br /><br /> \<Operation Name="Op1" Action="http://contoso.com/Svc/Op1" /\><br /><br /> \<Operation Name="Op2" Action="http://contoso.com/Svc/Op2" /\><br /><br /> \</BtsActionMapping\><br /><br /> If outgoing messages come from an orchestration port, orchestration instances dynamically set the **BTS.Operation** property with the operation name of the port. If outgoing messages are routed with content-based routing, you can set the **BTS.Operation** property in pipeline components.<br /><br /> The default is an empty string.|  
|**BindingType**|Enum<br /><br /> For more information about the member names for the **BindingType** property, see the **Binding Type** property in the **WCF-Custom Transport Properties Dialog Box, Send, Binding** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Specify the type of the binding to use for the endpoint that this send port uses. **Note:**  If you use a custom binding, the **BindingType** property can be configured with the custom bindings. For more information about how to use custom binding, see [How to Enable the WCF Extensibility Points with the WCF Adapters](../core/how-to-enable-the-wcf-extensibility-points-with-the-wcf-adapters.md).|  
|**BindingConfiguration**|XML Blob<br /><br /> Example:<br /><br /> &lt;binding name="netNamedPipeBinding"&gt;&lt;readerQuotas maxDepth="32" maxStringContentLength="8192" maxArrayLength="16384" maxBytesPerRead="4096" maxNameTableCharCount="16384" /&gt;&lt;security mode="None" /&gt;&lt;/binding&gt;|Specify an XML string with the **\<binding\>** element to configure different types of predefined bindings provided by Windows Communication Foundation (WCF). For more information about the system-provided binding and custom binding, see the appropriate topics listed in See Also. **Note:**  BizTalk Server does not support all the types of the binding extension elements that you can configure with the **BindingConfiguration** property. <br /><br /> The default is an empty string.|  
|**EndpointBehaviorConfiguration**|XML Blob<br /><br /> Example:<br /><br /> &lt;behavior name="sampleBehavior"&gt;&lt;callbackTimeouts /&gt;&lt;/behavior&gt;|Specify an XML string with the **\<behavior\>** element of the **\<endpointBehaviors\>** element to configure the behavior settings of a WCF endpoint. For more information about the **\<endpointBehaviors\>** element, see the appropriate topic in See Also. **Note:**  BizTalk Server does not support all the types of the behavior extension elements that you can configure with the **EndpointBehaviorConfiguration** property. <br /><br /> The default is an empty string.|  
|**AffiliateApplicationName**|String|Specify the affiliate application to use for Enterprise Single Sign-On (SSO).<br /><br /> The default is an empty string.|  
|**UseSSO**|Boolean|Specify whether to use Single Sign-On to retrieve client credentials for authentication with the destination server.<br /><br /> Default value: **False**|  
|**UserName**|String|Specify the user name to use for authentication with the destination server when the **UseSSO** property is set to **False**. You do not have to use the domain\user format for this property.<br /><br /> The default is an empty string.|  
|**Password**|String|Specify the password to use for authentication with the destination server when the **UseSSO** property is set to **False**.<br /><br /> The default is an empty string.|  
|**OutboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** - Use the BizTalk message body part to create the content of the SOAP **Body** element for an outgoing message.<br />-   **UseTemplate** - Use the template supplied in the **OutboundXMLTemplate** property to create the content of the SOAP **Body** element for an outgoing message.<br /><br /> For more information about how to use the **OutboundBodyLocation** property, see [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Specify the data selection for the SOAP **Body** element of outgoing WCF messages.<br /><br /> Default value: **UseBodyElement**|  
|**OutboundXMLTemplate**|String<br /><br /> For more information about how to use the **OutboundXMLTemplate** property, see [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Specify the XML-formatted template for the content of the SOAP **Body** element of an outgoing message. This property is required if the **OutboundBodyLocation** property is set to **UseTemplate**.<br /><br /> The default is an empty string.|  
|**InboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** - Use the content of the SOAP **Body** element of an incoming message to create the BizTalk message body part. If the **Body** element has more than one child element, only the first element becomes the BizTalk message body part. This property is valid only for solicit-response ports.<br />-   **UseEnvelope** - Create the BizTalk message body part from the entire SOAP **Envelope** of an incoming message.<br />-   **UseBodyPath** - Use the body path expression in the **InboundBodyPathExpression** property to create the BizTalk message body part. The body path expression is evaluated against the immediate child element of the SOAP **Body** element of an incoming message. This property is valid only for solicit-response ports.<br /><br /> For more information about how to use the **InboundBodyLocation** property, see [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Specify the data selection for the SOAP **Body** element of incoming WCF messages.<br /><br /> Default value: **UseBodyElement**|  
|**InboundBodyPathExpression**|String<br /><br /> For more information about how to use the **InboundBodyPathExpression** property, see [WCF Adapters Property Schema and Properties](../core/wcf-adapters-property-schema-and-properties.md).|Specify the body path expression to identify a specific part of an incoming message used to create the BizTalk message body part. This body path expression is evaluated against the immediate child element of the SOAP **Body** node of an incoming message. If this body path expression returns more than one node, only the first node is chosen for the BizTalk message body part. This property is required if the **InboundBodyLocation** property is set to **UseBodyPath**. This property is valid only for solicit-response ports.<br /><br /> The default is an empty string.|  
|**InboundNodeEncoding**|Enum<br /><br /> -   **XML**<br />-   **Base64** - Base64 encoding.<br />-   **Hex** - Hexadecimal encoding.<br />-   **String** - Text encoding - UTF-8.<br />-   **XML** - The WCF adapters create the BizTalk message body with the outer XML of the node selected by the body path expression in **InboundBodyPathExpression**.|Specify the type of encoding that the WCF-Custom send adapter uses to decode for the node identified by the body path specified in **InboundBodyPathExpression**. This property is required if the **InboundBodyLocation** property is set to **UseBodyPath**. This property is valid only for solicit-response ports.<br /><br /> Default value: **XML**|  
|**PropagateFaultMessage**|Boolean<br /><br /> -   **True** - Route the message that fails outbound processing to a subscribing application (such as another receive port or orchestration schedule).<br />-   **False** - Suspend failed messages and generate a negative acknowledgment (NACK).|Specify whether to route or suspend messages failed in outbound processing.<br /><br /> This property is valid only for solicit-response ports.<br /><br /> Default value: **True**|  
|**ReferencedBindings**|XML Blob<br /><br /> Example:<br /><br /> \<**BindingConfiguration** vt="8"\><br /><br /> &lt;wsFederationHttpBinding&gt;<br /><br /> &lt;binding name="sampleBinding"&gt;<br /><br /> &lt;security mode="Message"&gt;<br /><br /> &lt;message issuedKeyType="AsymmetricKey"&gt;<br /><br /> &lt;issuer address="http://www.contoso.com/samplests" binding="wsFederationHttpBinding" bindingConfiguration="**contosoSTSBinding**"/&gt;<br /><br /> &lt;/message&gt;<br /><br /> &lt;/security&gt;<br /><br /> &lt;/binding&gt;<br /><br /> &lt;/wsFederationHttpBinding&gt;<br /><br /> \</**BindingConfiguration**\><br /><br /> \<**ReferencedBindings** vt="8"\><br /><br /> &lt;bindings&gt;<br /><br /> &lt;wsFederationHttpBinding&gt;<br /><br /> &lt;binding name="**contosoSTSBinding**"&gt;<br /><br /> &lt;security mode="Message"&gt;<br /><br /> &lt;message negotiateServiceCredential="false"&gt;<br /><br /> &lt;issuer address="http://northwind.com/samplests" bindingConfiguration="**northwindBinding**" binding="wsHttpBinding"&gt;<br /><br /> &lt;/issuer&gt;<br /><br /> &lt;/message&gt;<br /><br /> &lt;/security&gt;<br /><br /> &lt;/binding&gt;<br /><br /> &lt;/wsFederationHttpBinding&gt;<br /><br /> &lt;wsHttpBinding&gt;<br /><br /> &lt;binding name="**northwindBinding**"&gt;<br /><br /> &lt;security mode="Message"&gt;<br /><br /> &lt;message clientCredentialType="Certificate" /&gt;<br /><br /> &lt;/security&gt;<br /><br /> &lt;/binding&gt;<br /><br /> &lt;/wsHttpBinding&gt;<br /><br /> &lt;/bindings&gt;<br /><br /> \</**ReferencedBindings**\> **Note:**  The **ReferencedBinding** property must not contain the binding configuration used in the **BindingConfiguration** property.|Specify the binding configurations referenced by the **bindingConfiguration** attribute of the **\<issuer\>** element for the **wsFederationHttpBinding** and **customBinding**, which indicates the Security Token Service (STS) that issues security tokens. For more information about the **\<issuer\>** element, see the topic, "\<issuer\>" at [http://go.microsoft.com/fwlink/?LinkId=83476](http://go.microsoft.com/fwlink/?LinkId=83476).<br /><br /> The binding information including the **\<issuer\>** element for the **wsFederationHttpBinding** and **customBinding** can be configured through the **BindingConfiguration** property of the WCF-Custom and the WCF-CustomIsolated adapters. All of the referenced binding configurations for this property must be placed in the form of the [\<bindings\>](http://go.microsoft.com/fwlink/?LinkID=80878) element. **Note:**  You cannot configure this property on the **Binding** tab in the transport properties dialog box. You can import and export this property through the **Import/Export** tab in the transport properties dialog box of the WCF-Custom and WCF-CustomIsolated adapters. **Note:**  The **bindingConfiguration** attribute of the **\<issuer\>** element must refer a valid binding name in this property. **Note:**  The **\<issuer\>** element in the referenced binding configurations can also refer to a different binding configuration in t his property if this reference chain does not make a circular dependency. <br /><br /> The default is an empty string.|  
  
## Configure a WCF-Custom Send Port with the BizTalk Administration Console
  
 You can set WCF-Custom send port adapter variables in the BizTalk Administration console. If properties are not set for the send port, the default values for the WCF-Custom send port configuration are used, as indicated in the previous table.  
  
## Configure variables for a WCF-Custom send port  
  
1.  If you plan to use the WCF extensibility points such as the custom binding elements, custom behavior element, and custom channel components when configuring the WCF-Custom adapter, you must add the assemblies that implement the extensibility points and all of the dependent assemblies to the global assembly cache on both the BizTalk processing computer (runtime computer) and the administration computer. In addition, you must register the extension components to the machine.config file. For more information about how to use the WCF extensibility points with the WCF Custom adapter, see [How to Enable the WCF Extensibility Points with the WCF Adapters](../core/how-to-enable-the-wcf-extensibility-points-with-the-wcf-adapters.md).  
  
2.  In the BizTalk Administration console, create a new send port or double-click an existing send port to modify it. For more information, see [How to Create a Send Port](../core/how-to-create-a-send-port2.md). Configure all of the send port options and specify **WCF-Custom** for the **Type** option in the **Transport** section of the **General** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
3.  On the **General** tab, in the **Transport** section, click the **Configure** button next to **Type**.  
  
4.  In the **WCF-Custom Transport Properties** dialog box, on the **General** tab, configure the endpoint address, the service identity, and the **SOAPAction** header for the WCF-Custom send port. For more information about the **General** tab in the **WCF-Custom Transport Properties** dialog box, see the **WCF-Custom Transport Properties Dialog Box, Send, General** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
5.  In the **WCF-Custom Transport Properties** dialog box, on the **Binding** tab, configure different types of predefined or custom bindings for WCF. For more information about the **Binding** tab in the **WCF-Custom Transport Properties** dialog box, see the **WCF-Custom Transport Properties Dialog Box, Send, Binding** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
6.  In the **WCF-Custom Transport Properties** dialog box, on the **Behavior** tab, configure the endpoint behavior for this send port. An endpoint behavior is a set of the behavior extension elements that modify or extend service or client functionality. For more information about the **Behavior** tab in the **WCF-Custom Transport Properties** dialog box, see the **WCF-Custom Transport Properties Dialog Box, Send, Behavior** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
7.  In the **WCF-Custom Transport Properties** dialog box, on the **Credentials** tab, specify the credentials to be used when sending messages. For more information about the **Credentials** tab in the **WCF-Custom Transport Properties** dialog box see the **WCF-Custom Transport Properties Dialog Box, Send, Credentials** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
8.  In the **WCF-Custom Transport Properties** dialog box, on the **Messages** tab, specify the data selection for the SOAP **Body** element. For more information about the **Messages** tab in the **WCF-Custom Transport Properties** dialog box, see the **WCF-Custom Transport Properties Dialog Box, Send, Messages** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
9. In the **WCF-Custom Transport Properties** dialog box, on the **Import/Export** tab, import and export the **Address (URI)** and **Endpoint Identity** properties on the **General** tab, binding information on the **Binding** tab, and endpoint behavior on the **Behavior** tab for this send port. For more information about the **Import/Export** tab in the **WCF-Custom Transport Properties** dialog box, see the **WCF-Custom Transport Properties Dialog Box, Send, Import-Export** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
## Configure a WCF-Custom Send Port programmatically  
  
 You can use the following format to set the properties:  
  
```  
<CustomProps>  
  <OutboundXmlTemplate vt="8"><bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="xml"/></OutboundXmlTemplate>  
  <InboundBodyPathExpression vt="8" />  
  <EndpointBehaviorConfiguration vt="8"><behavior name="sampleBehavior"><callbackTimeouts /></behavior></EndpointBehaviorConfiguration>  
  <OutboundBodyLocation vt="8">UseBodyElement</OutboundBodyLocation>  
  <StaticAction vt="8">http://www.northwindtraders.com/Service/Operation</StaticAction>  
  <BindingConfiguration vt="8"><binding name="NetNamedPipeOrderProcessService.OrderProcessServieEndpoint"><readerQuotas maxDepth="32" maxStringContentLength="8192" maxArrayLength="16384" maxBytesPerRead="4096" maxNameTableCharCount="16384" /><security mode="None" /></binding></BindingConfiguration>  
  <InboundNodeEncoding vt="8">Xml</InboundNodeEncoding>  
  <UseSSO vt="11">0</UseSSO>  
  <AffiliateApplicationName vt="8" />  
  <BindingType vt="8">netNamedPipeBinding</BindingType>  
  <InboundBodyLocation vt="8">UseBodyElement</InboundBodyLocation>  
  <UserName vt="8" />  
  <PropagateFaultMessage vt="11">-1</PropagateFaultMessage>  
</CustomProps>  
  
```  
  
 The following code fragment illustrates creating a WCF-Custom send port:  
  
```  
// Use BizTalk Explorer object model to create new WCF-Custom send port.  
string server = System.Environment.MachineName;  
string database = "BizTalkMgmtDb";  
string connectionString = string.Format("Server={0};Database={1};Integrated Security=true", server, database);  
string transportConfigData = @"<CustomProps>  
                                 <StaticAction vt=""8"">http://www.northwindtraders.com/Service/Operation</StaticAction>  
                                 <EndpointBehaviorConfiguration vt=""8""><behavior name=""sampleBehavior""><callbackTimeouts /></behavior></EndpointBehaviorConfiguration>  
                                 <BindingType vt=""8"">netNamedPipeBinding</BindingType>  
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
sendPort.PrimaryTransport.TransportType = explorer.ProtocolTypes["WCF-Custom"];  
sendPort.PrimaryTransport.Address = "net.pipe://mycomputer/private/samplequeue";  
sendPort.PrimaryTransport.TransportTypeData = transportConfigData; // propertyData; // need to change  
sendPort.SendPipeline = explorer.Pipelines["Microsoft.BizTalk.DefaultPipelines.PassThruTransmit"];  
// Save  
explorer.SaveChanges();  
```  
  
## See Also  
 [WCF Adapters Property Schema and Properties](../core/wcf-adapters-property-schema-and-properties.md)   
 [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md)   
 [Installing Certificates for the WCF Adapters](../core/installing-certificates-for-the-wcf-adapters.md)   
 [Configuring the WCF-Custom Adapter](../core/configuring-the-wcf-custom-adapter.md)   
 [Configuring Dynamic Send Ports Using WCF Adapters Context Properties](../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)   
 [\<bindings\>](http://go.microsoft.com/fwlink/?LinkId=80878)   
 [\<behavior\> of \<endpointBehaviors\>](http://go.microsoft.com/fwlink/?LinkId=80879)