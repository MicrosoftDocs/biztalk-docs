---
title: "How to Configure a WCF-Custom Receive Location | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e2092cd4-6612-4ac3-81f3-dd25438837ae
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure a WCF-Custom Receive Location
You can configure a WCF-Custom receive location either programmatically or by using the BizTalk Administration console.  
  
## Configuration properties
  
 The BizTalk Explorer Object Model enables you to create and configure receive locations programmatically. The BizTalk Explorer Object Model exposes the**IReceiveLocation** receive location configuration interface that has a **TransportTypeData** read/write property. This property accepts a WCF-Custom receive location configuration property bag in the form of a name-value pair of XML strings. To set this property in the BizTalk Explorer Object Model, you must set the **InboundTransportLocation** property of the **IReceiveLocation** interface.  
  
 The **TransportTypeData** property of the **IReceiveLocation** interface does not have to be set. If it is not set, the WCF-Custom adapter uses the default values for the WCF-Custom receive location configuration as indicated in the following table.  
  
 The following table lists the configuration properties that you can set in the BizTalk Explorer Object Model for the WCF-Custom receive location.  
  
|Property name|Type|Description|  
|-------------------|----------|-----------------|  
|**Identity**|XML Blob<br /><br /> Example:<br /><br /> &lt;identity&gt;<br /><br /> &lt;userPrincipalName value="username@contoso.com" /&gt;<br /><br /> &lt;/identity&gt;|Specify the identity of the service that this receive location provides. The values that can be specified for the **Identity** property differ according to the security configuration. These settings enable the client to authenticate this receive location. In the handshake process between the client and service, the Windows Communication Foundation (WCF) infrastructure will ensure that the identity of the expected service matches the values of this element.<br /><br /> The default is an empty string.|  
|**BindingType**|Enum<br /><br /> -   **basicHttpBinding**<br />-   **customBinding**<br />-   **mexHttpBinding**<br />-   **mexHttpsBinding**<br />-   **mexNamedPipeBinding**<br />-   **mexTcpBinding**<br />-   **netMsmqBinding**<br />-   **netNamedPipeBinding**<br />-   **netPeerTcpBinding**<br />-   **netTcpBinding**<br />-   **wsDualHttpBinding**<br />-   **wsFederationHttpBinding**<br />-   **wsHttpBinding**|Specify the type of the binding to use for the endpoint that this receive location uses. **Note:**  If you use a custom binding, the **BindingType** property can be configured with the custom bindings. For more information about how to use custom binding, see [How to Enable the WCF Extensibility Points with the WCF Adapters](../core/how-to-enable-the-wcf-extensibility-points-with-the-wcf-adapters.md). <br /><br /> The default is an empty string.|  
|**BindingConfiguration**|XML Blob<br /><br /> Example:<br /><br /> &lt;binding name="netNamedPipeBinding"&gt;&lt;security mode="None" /&gt;&lt;/binding&gt;|Specify an XML string with the **\<binding\>** element to configure different types of predefined bindings provided by Windows Communication Foundation (WCF). For more information about the system-provided binding and custom binding, see the appropriate topics in See Also. **Note:**  BizTalk Server does not support all the types of the binding extension elements that you can configure with the **BindingConfiguration** property. <br /><br /> The default is an empty string.|  
|**ServiceBehaviorConfiguration**|XML Blob<br /><br /> Example:<br /><br /> &lt;behavior name="SampleServiceBehavior"&gt;&lt;serviceMetadata httpGetEnabled="true" httpGetUrl="http://mycomputer:9995/SampleMex" /&gt;&lt;serviceCredentials /&gt;&lt;/behavior&gt;|Specify an XML string with the **\<behavior\>** element of the **\<serviceBehaviors\>** element to configure the behavior settings of a WCF service. For more information about the **\<serviceBehaviors\>** element, see the appropriate topic in See Also.<br /><br /> The default is an empty string.|  
|**EndpointBehaviorConfiguration**|XML Blob<br /><br /> Example:<br /><br /> &lt;behavior name="sampleBehavior"&gt;&lt;callbackTimeouts /&gt;&lt;/behavior&gt;|Specify an XML string with the **\<behavior\>** element of the **\<endpointBehaviors\>** element to configure the behavior settings of a WCF endpoint. For more information about the **\<endpointBehaviors\>** element, see the appropriate topic in See Also. **Note:**  BizTalk Server does not support all the types of the behavior extension elements that you can configure with the **EndpointBehaviorConfiguration** property. <br /><br /> The default is an empty string.|  
|**CredentialType**|Enum<br /><br /> -   **None**: Do not use any credentials when this receive location sends solicit messages to poll an external service, or this receive location does not need to poll any external service.<br />-   **IssueTicket**: Use Enterprise Single Sign-On (SSO) to retrieve client credentials to issue an SSO ticket. This option requires using the security mode that allows this receive location to impersonate the user account to issue an SSO ticket.<br />-   **UserAccount**: Use the credentials specified in the **Username** and **Password** properties when this receive location sends solicit messages to poll an external service.<br />-   **GetCredentials**: Use the SSO affiliate application specified in the **AffiliateApplicationName** property when this receive location sends solicit messages to poll an external service.|Specify the type of credentials for this receive location to use when polling an external service<br /><br /> Default value: **None**|  
|**UserName**|String|Specify the user name for this receive location to use when polling an external service to retrieve response messages. This property is required when the **CredentialType** property is set to **UserAccount**.<br /><br /> The default is an empty string.|  
|**Password**|String|Specify the password for this receive location to use when polling an external service to retrieve response messages. This property is required when the **CredentialType** property is set to **UserAccount**.<br /><br /> The default is an empty string.|  
|**AffiliateApplicationName**|String|Specify the SSO affiliate application to return external credentials to be used when this receive location sends solicit messages to poll an external service. The specified SSO affiliate application must have a mapping between the Windows account under which this receive location runs and the account for the external service. This property is required when the **CredentialType** property is set to **GetCredentials**.<br /><br /> The default is an empty string.|  
|**OrderedProcessing**|Boolean|Specify whether to preserve message order when processing messages (for use with the NetMsmq binding).<br /><br /> Default value: **False**|  
|**InboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** - Use the content of the SOAP **Body** element of an incoming message to create the BizTalk message body part. If the **Body** element has more than one child element, only the first element becomes the BizTalk message body part.<br />-   **UseEnvelope** - Create the BizTalk message body part from the entire SOAP **Envelope** of an incoming message.<br />-   **UseBodyPath** - Use the body path expression in the **InboundBodyPathExpression** property to create the BizTalk message body part. The body path expression is evaluated against the immediate child element of the SOAP **Body** element of an incoming message. This property is valid only for solicit-response ports.<br /><br /> For more information about how to use the **InboundBodyLocation** property, see [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Specify the data selection for the SOAP **Body** element of incoming WCF messages.<br /><br /> Default value: **UseBodyElement**|  
|**InboundBodyPathExpression**|String<br /><br /> For more information about how to use the **InboundBodyPathExpression** property, see [WCF Adapters Property Schema and Properties](../core/wcf-adapters-property-schema-and-properties.md).|Specify the body path expression to identify a specific part of an incoming message used to create the BizTalk message body part. This body path expression is evaluated against the immediate child element of the SOAP **Body** node of an incoming message. If this body path expression returns more than one node, only the first node is chosen for the BizTalk message body part. This property is required if the **InboundBodyLocation** property is set to **UseBodyPath**.<br /><br /> The default is an empty string.|  
|**InboundNodeEncoding**|Enum<br /><br /> -   **Base64** - Base64 encoding.<br />-   **Hex** - Hexadecimal encoding.<br />-   **String** - Text encoding - UTF-8.<br />-   **XML** - The WCF adapters create the BizTalk message body with the outer XML of the node selected by the body path expression in **InboundBodyPathExpression**.|Specify the type of encoding that the WCF-Custom receive adapter uses to decode the node identified by the body path expression specified in **InboundBodyPathExpression**. This property is required if the **InboundBodyLocation** property is set to **UseBodyPath**.<br /><br /> Default value: **XML**|  
|**OutboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** - Use the BizTalk message body part to create the content of the SOAP **Body** element for an outgoing response message.<br />-   **UseTemplate** - Use the template supplied in the **OutboundXMLTemplate** property to create the content of the SOAP **Body** element for an outgoing response message.<br /><br /> For more information about how to use the **OutboundBodyLocation** property, see [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Specify the data selection for the SOAP **Body** element of outgoing WCF messages. This property is valid only for request-response receive locations.<br /><br /> Default value: **UseBodyElement**|  
|**OutboundXMLTemplate**|String<br /><br /> For more information about how to use the **OutboundXMLTemplate** property, see [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Specify the XML-formatted template for the content of the SOAP **Body** element of an outgoing response message. This property is required if the **OutboundBodyLocation** property is set to **UseTemplate**. This property is valid only for request-response receive locations.<br /><br /> The default is an empty string.|  
|**DisableLocationOnFailure**|Boolean|Specify whether to disable the receive location that fails inbound processing due to a receive pipeline failure or a routing failure.<br /><br /> Default: **False**|  
|**SuspendMessageOnFailure**|Boolean|Specify whether to suspend the request message that fails inbound processing due to a receive pipeline failure or a routing failure.<br /><br /> Default value: **True**|  
|**IncludeExceptionDetailInFaults**|Boolean|Specify whether to include managed exception information in the detail of SOAP faults returned to the client for debugging purposes.<br /><br /> Default: **False**|  
|**ReferencedBindings**|XML Blob<br /><br /> Example:<br /><br /> \<**BindingConfiguration** vt="8"\><br /><br /> &lt;wsFederationHttpBinding&gt;<br /><br /> &lt;binding name="sampleBinding"&gt;<br /><br /> &lt;security mode="Message"&gt;<br /><br /> &lt;message issuedKeyType="AsymmetricKey"&gt;<br /><br /> &lt;issuer address="http://www.contoso.com/samplests" binding="wsFederationHttpBinding" bindingConfiguration="**contosoSTSBinding**"/&gt;<br /><br /> &lt;/message&gt;<br /><br /> &lt;/security&gt;<br /><br /> &lt;/binding&gt;<br /><br /> &lt;/wsFederationHttpBinding&gt;<br /><br /> \</**BindingConfiguration**\><br /><br /> \<**ReferencedBindings** vt="8"\><br /><br /> &lt;bindings&gt;<br /><br /> &lt;wsFederationHttpBinding&gt;<br /><br /> &lt;binding name="**contosoSTSBinding**"&gt;<br /><br /> &lt;security mode="Message"&gt;<br /><br /> &lt;message negotiateServiceCredential="false"&gt;<br /><br /> &lt;issuer address="http://northwind.com/samplests" bindingConfiguration="**northwindBinding**" binding="wsHttpBinding"&gt;<br /><br /> &lt;/issuer&gt;<br /><br /> &lt;/message&gt;<br /><br /> &lt;/security&gt;<br /><br /> &lt;/binding&gt;<br /><br /> &lt;/wsFederationHttpBinding&gt;<br /><br /> &lt;wsHttpBinding&gt;<br /><br /> &lt;binding name="**northwindBinding**"&gt;<br /><br /> &lt;security mode="Message"&gt;<br /><br /> &lt;message clientCredentialType="Certificate" /&gt;<br /><br /> &lt;/security&gt;<br /><br /> &lt;/binding&gt;<br /><br /> &lt;/wsHttpBinding&gt;<br /><br /> &lt;/bindings&gt;<br /><br /> \</**ReferencedBindings**\> **Note:**  The **ReferencedBinding** property must not contain the binding configuration used in the **BindingConfiguration** property.|Specify the binding configurations referenced by the **bindingConfiguration** attribute of the **\<issuer\>** element for the **wsFederationHttpBinding** and **customBinding**, which indicates the Security Token Service (STS) that issues security tokens. For more information about the **\<issuer\>** element, see the topic, "\<issuer\>" at [http://go.microsoft.com/fwlink/?LinkId=83476](http://go.microsoft.com/fwlink/?LinkId=83476).<br /><br /> The binding information including the **\<issuer\>** element for the **wsFederationHttpBinding** and **customBinding** can be configured through the **BindingConfiguration** property of the WCF-Custom and the WCF-CustomIsolated adapters. All of the referenced binding configurations for this property must be placed in the form of the [\<bindings\>](http://go.microsoft.com/fwlink/?LinkID=80878) element. **Note:**  You cannot configure this property on the **Binding** tab in the transport properties dialog box. You can import and export this property through the **Import/Export** tab in the transport properties dialog box of the WCF-Custom and WCF-CustomIsolated adapters. **Note:**  The **bindingConfiguration** attribute of the **\<issuer\>** element must refer a valid binding name in this property. **Note:**  The **\<issuer\>** element in the referenced binding configurations can also refer to a different binding configuration in t his property if this reference chain does not make a circular dependency. <br /><br /> The default is an empty string.|  
  
## Configure a WCF-Custom Receive Location with the BizTalk Administration Console
  
 You can set WCF-Custom receive location adapter variables in the BizTalk Administration console. If properties are not set in the receive location, the default receive handler values set in the BizTalk Administration console are used.  
  
> [!NOTE]
>  Before completing the following procedure you must have already added a receive port. For more information, see [How to Create a Receive Port](../core/how-to-create-a-receive-port.md).  
  
## Configure variables for a WCF-Custom receive location  
  
1.  If you plan to use the WCF extensibility points such as the custom binding elements, custom behavior element, and custom channel components when configuring the WCF-Custom adapter, you must add the assemblies that implement the extensibility points and all of the dependent assemblies to the global assembly cache on both the BizTalk processing computer (runtime computer) and the administration computer. In addition, you must register the extension components to the machine.config file. For more information about how to use the WCF extensibility points with the WCF Custom adapter, see [How to Enable the WCF Extensibility Points with the WCF Adapters](../core/how-to-enable-the-wcf-extensibility-points-with-the-wcf-adapters.md).  
  
2.  In the BizTalk Administration console, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, expand **Applications**, and then expand the application in which you want to create a receive location.  
  
3.  In the BizTalk Administration console, in the left pane, click the **Receive Port** node. Then in the right pane, right-click the receive port that is associated with an existing receive location or that you want to associate with a new receive location, and then click **Properties**.  
  
4.  In the **Receive Port Properties** dialog box, in the left pane, select **Receive Locations**, and then in the right pane, double-click an existing receive location or click **New**to create a new receive location.  
  
5.  In the **Receive Location Properties** dialog box, in the **Transport** section next to **Type**, select **WCF-Custom** from the drop-down list, and then click **Configure**.  
  
6.  In the **WCF-Custom Transport Properties** dialog box, on the **General** tab, configure the endpoint address and the service identity for the WCF-Custom receive location. For more information about the **General** tab in the **WCF-Custom Transport Properties** dialog box, see the **WCF-Custom Transport Properties Dialog Box, Receive, General** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
7.  In the **WCF-Custom Transport Properties** dialog box, on the **Binding** tab, configure different types of predefined or custom bindings for WCF. For more information about the **Binding** tab in the **WCF-Custom Transport Properties** dialog box, see the **WCF-Custom Transport Properties Dialog Box, Receive, Binding** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
8.  In the **WCF-Custom Transport Properties** dialog box, on the **Behavior** tab, configure the endpoint and service behaviors for this receive location. An endpoint behavior is a set of behavior extension elements that modify or extend service or client functionality. For more information about the **Behavior** tab in the **WCF-Custom Transport Properties** dialog box, see the **WCF-Custom Transport Properties Dialog Box, Receive, Behavior** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
9. In the **WCF-Custom Transport Properties** dialog box, on the **Other** tab, configure which credentials for this receive location to use when polling an external service, and whether this receive location preserves message order when processing messages. For more information about the **Other** tab in the **WCF-Custom Transport Properties** dialog box, see the **WCF-Custom Transport Properties Dialog Box, Receive, Other** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
10. In the **WCF-Custom Transport Properties** dialog box, on the **Messages** tab, specify the data selection for the SOAP **Body** element. For more information about the **Messages** tab in the **WCF-Custom Transport Properties** dialog box, see the **WCF-Custom Transport Properties Dialog Box, Receive, Messages** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
11. In the **WCF-Custom Transport Properties** dialog box, on the **Import/Export** tab, import and export the **Address (URI)** and **Endpoint Identity** properties on the **General** tab, binding information on the **Binding** tab, and endpoint behavior on the **Behavior** tab for this receive location. For more information about the **Import/Export** tab in the **WCF-Custom Transport Properties** dialog box, see the **WCF-Custom Transport Properties Dialog Box, Receive, Import-Export** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  

## Configure a WCF-Custom Receive Location programmatically
  
 You can use the following format to set the properties:  
  
```  
<CustomProps>  
  <InboundBodyPathExpression vt="8" />  
  <InboundBodyLocation vt="8">UseBodyElement</InboundBodyLocation>  
  <BindingConfiguration vt="8"><binding name="netNamedPipeBinding"><security mode="None" /></binding></BindingConfiguration>  
  <OutboundXmlTemplate vt="8"><bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="xml"/></OutboundXmlTemplate>  
  <CredentialType vt="8">GetCredentials</CredentialType>  
  <Identity vt="8" />  
  <ServiceBehaviorConfiguration vt="8"><behavior name="SampleServiceBehavior"><serviceMetadata httpGetEnabled="true" httpGetUrl="http://mycomputer:9995/SampleService/Mex" /><serviceCredentials /></behavior></ServiceBehaviorConfiguration>  
  <Password vt="1" />  
  <OrderedProcessing vt="11">-1</OrderedProcessing>  
  <IncludeExceptionDetailInFaults vt="11">0</IncludeExceptionDetailInFaults>  
  <AffiliateApplicationName vt="8">SampleAffiliateApplication</AffiliateApplicationName>  
  <DisableLocationOnFailure vt="11">0</DisableLocationOnFailure>  
  <SuspendMessageOnFailure vt="11">0</SuspendMessageOnFailure>  
  <BindingType vt="8">netNamedPipeBinding</BindingType>  
  <UserName vt="8">Hello</UserName>  
  <InboundNodeEncoding vt="8">Xml</InboundNodeEncoding>  
  <EndpointBehaviorConfiguration vt="8"><behavior name="EndpointBehavior" /></EndpointBehaviorConfiguration>  
  <OutboundBodyLocation vt="8">UseBodyElement</OutboundBodyLocation>  
</CustomProps>  
  
```  
  
 The following code fragment illustrates creating a WCF-Custom receive location:  
  
```  
// Use BizTalk Explorer object model to create new WCF-Custom receive location   
string server = System.Environment.MachineName;  
string database = "BizTalkMgmtDb";  
string connectionString = string.Format("Server={0};Database={1};Integrated Security=true", server, database);  
string transportConfigData = @"<CustomProps>  
  <BindingConfiguration vt=""8""><binding name=""netNamedPipeBinding""><security mode=""None"" /></binding></BindingConfiguration>  
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
  
// Add a new one-way receive port  
IReceivePort receivePort = application.AddNewReceivePort(false);  
receivePort.Name = "SampleReceivePort";  
// Add a new one-way receive location  
IReceiveLocation recieveLocation = receivePort.AddNewReceiveLocation();  
recieveLocation.Name = "SampleReceiveLocation";  
// Find a receive handler for WCF-Custom   
int i = 0;  
for(i=0; i < explorer.ReceiveHandlers.Count; ++i)   
{  
    if("WCF-Custom" == explorer.ReceiveHandlers[i].TransportType.Name)  
        break;  
}  
recieveLocation.ReceiveHandler = explorer.ReceiveHandlers[i];  
recieveLocation.Address = "net.pipe://mycomputer/samplePipeName";  
recieveLocation.ReceivePipeline = explorer.Pipelines["Microsoft.BizTalk.DefaultPipelines.PassThruReceive"];  
recieveLocation.TransportType = explorer.ProtocolTypes["WCF-Custom"];  
recieveLocation.TransportTypeData = transportConfigData;  
// Save  
explorer.SaveChanges();   
```  
  
## See Also  
 [Publishing Service Metadata for the WCF Receive Adapters](../core/publishing-service-metadata-for-the-wcf-receive-adapters.md)   
 [Managing BizTalk Hosts and Host Instances](../core/managing-biztalk-hosts-and-host-instances.md)   
 [How to Change Service Accounts and Passwords](../core/how-to-change-service-accounts-and-passwords.md)   
 [Installing Certificates for the WCF Adapters](../core/installing-certificates-for-the-wcf-adapters.md)   
 [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md)   
 [Configuring the WCF-Custom Adapter](../core/configuring-the-wcf-custom-adapter.md)   
 [How to Create an Affiliate Application](../core/how-to-create-an-affiliate-application.md)   
 [\<behavior\> of \<endpointBehaviors\>](http://go.microsoft.com/fwlink/?LinkId=80879)   
 [\<bindings\>](http://go.microsoft.com/fwlink/?LinkId=80878)   
 [\<behavior\> of \<serviceBehaviors\>](http://go.microsoft.com/fwlink/?LinkId=81095)