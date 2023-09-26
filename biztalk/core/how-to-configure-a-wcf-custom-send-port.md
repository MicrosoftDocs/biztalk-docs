---
description: "Learn more about: How to Configure a WCF-Custom Send Port"
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

 The following list describes the configuration properties you can set in the BizTalk Explorer Object Model for WCF-Custom send ports:

- **Property name**: **Identity**  
  - **Type**: XML Blob

    Example: 

    ```xml
    <identity>
     <userPrincipalName value="username@contoso.com" />
    </identity>
    ```

  - **Description**: Specify the identity of the service that this send port expects. These settings enable this send port to authenticate the service. In the handshake process between the client and service, the WCF infrastructure will ensure that the identity of the expected service matches the values of this element. The values that can be specified for the **Identity** property differ according to the security configuration.

    The default is an empty string.

- **Property name**: **StaticAction**
  - **Type**: String
  - **Description**: Specify the **SOAPAction** header field for outgoing messages. This property can also be set through the message context property **WCF.Action** in a pipeline or orchestration. You can specify this value in two different ways: the single action format and the action mapping format. If you set this property in the single action format, like `http://contoso.com/Svc/Op1`, then the **SOAPAction** header for outgoing messages is always set to the value specified in this property.

    If you set this property in the action mapping format, the outgoing **SOAPAction** header is determined by the **BTS.Operation** context property. For example, if this property is set to the following XML format and the **BTS.Operation** property is set to Op1, then the WCF send adapter uses `http://contoso.com/Svc/Op1` for the outgoing **SOAPAction** header.

    ```xml
    <BtsActionMapping>
     <Operation Name="Op1" Action="<http://contoso.com/Svc/Op1>" />
     <Operation Name="Op2" Action="<http://contoso.com/Svc/Op2>" />
    </BtsActionMapping>
    ```

    If outgoing messages come from an orchestration port, orchestration instances dynamically set the **BTS.Operation** property with the operation name of the port. If outgoing messages are routed with content-based routing, you can set the **BTS.Operation** property in pipeline components.

    The default is an empty string.

- **Property name**: **BindingType**
  - **Type**: Enum

    For more information about the member names for the **BindingType** property, see the **Binding Type** property in the **WCF-Custom Transport Properties Dialog Box, Send, Binding** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].

  - **Description**: Specify the type of the binding to use for the endpoint that this send port uses.

    If you use a custom binding, the **BindingType** property can be configured with the custom bindings. For more information about how to use custom binding, see [How to Enable the WCF Extensibility Points with the WCF Adapters](../core/how-to-enable-the-wcf-extensibility-points-with-the-wcf-adapters.md).

- **Property name**: **BindingConfiguration**
  - **Type**: XML Blob

    Example:

    ```xml
    <binding name="netNamedPipeBinding">
     <readerQuotas maxDepth="32" maxStringContentLength="8192" maxArrayLength="16384" maxBytesPerRead="4096" maxNameTableCharCount="16384" />
     <security mode="None" />
    </binding>
    ```    

  - **Description**: Specify an XML string with the `<binding>` element to configure different types of predefined bindings provided by Windows Communication Foundation (WCF). For more information about the system-provided binding and custom binding, see the appropriate topics listed in See Also.

    BizTalk Server does not support all the types of the binding extension elements that you can configure with the **BindingConfiguration** property.

    The default is an empty string.

- **Property name**: **EndpointBehaviorConfiguration**
  - **Type**: XML Blob

    Example:

    ```xml
    <behavior name="sampleBehavior">
     <callbackTimeouts />
    </behavior>
    ```

  - **Description**: Specify an XML string with the **`<behavior>`** element of the **`<endpointBehaviors>`** element to configure the behavior settings of a WCF endpoint. For more information about the **`<endpointBehaviors>`** element, see the appropriate topic in See Also.

    BizTalk Server does not support all the types of the behavior extension elements that you can configure with the **EndpointBehaviorConfiguration** property.

    The default is an empty string. 

- **Property name**: **AffiliateApplicationName**
  - **Type**: String
  - **Description**: Specify the affiliate application to use for Enterprise Single Sign-On (SSO).

    The default is an empty string.

- **Property name**: **UseSSO** 
  - **Type**: Boolean
  - **Description**: Specify whether to use Single Sign-On to retrieve client credentials for authentication with the destination server.

    Default value: **False**

- **Property name**: **UserName**
  - **Type**: String
  - **Description**:  Specify the user name to use for authentication with the destination server when the **UseSSO** property is set to **False**. You do not have to use the `domain\user` format for this property.

    The default is an empty string.

- **Property name**: **Password** 
  - **Type**: String
  - **Description**: Specify the password to use for authentication with the destination server when the **UseSSO** property is set to **False**.

    The default is an empty string.

- **Property name**: **OutboundBodyLocation**
  - **Type**: Enum
    - **UseBodyElement**: Use the BizTalk message body part to create the content of the SOAP **Body** element for an outgoing message.
    - **UseTemplate**: Use the template supplied in the **OutboundXMLTemplate** property to create the content of the SOAP **Body** element for an outgoing message.

    For more information about how to use the **OutboundBodyLocation** property, see [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md).

  - **Description**: Specify the data selection for the SOAP **Body** element of outgoing WCF messages.

    Default value: **UseBodyElement**

- **Property name**: **OutboundXMLTemplate**
  - **Type**: String

    For more information about how to use the **OutboundXMLTemplate** property, see [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md).
  - **Description**: Specify the XML-formatted template for the content of the SOAP **Body** element of an outgoing message. This property is required if the **OutboundBodyLocation** property is set to **UseTemplate**.

    The default is an empty string.

- **Property name**: **InboundBodyLocation**
  - **Type**: Enum
    - **UseBodyElement**: Use the content of the SOAP **Body** element of an incoming message to create the BizTalk message body part. If the **Body** element has more than one child element, only the first element becomes the BizTalk message body part. This property is valid only for solicit-response ports.
    - **UseEnvelope**: Create the BizTalk message body part from the entire SOAP **Envelope** of an incoming message.
    - **UseBodyPath**: Use the body path expression in the **InboundBodyPathExpression** property to create the BizTalk message body part. The body path expression is evaluated against the immediate child element of the SOAP **Body** element of an incoming message. This property is valid only for solicit-response ports.

    For more information about how to use the **InboundBodyLocation** property, see [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md).

  - **Description**: Specify the data selection for the SOAP **Body** element of incoming WCF messages.

    Default value: **UseBodyElement**

- **Property name**: **InboundBodyPathExpression**
  - **Type**: String

    For more information about how to use the **InboundBodyPathExpression** property, see [WCF Adapters Property Schema and Properties](../core/wcf-adapters-property-schema-and-properties.md).
  - **Description**: Specify the body path expression to identify a specific part of an incoming message used to create the BizTalk message body part. This body path expression is evaluated against the immediate child element of the SOAP **Body** node of an incoming message. If this body path expression returns more than one node, only the first node is chosen for the BizTalk message body part. This property is required if the **InboundBodyLocation** property is set to **UseBodyPath**. This property is valid only for solicit-response ports.

    The default is an empty string.

- **Property name**: **InboundNodeEncoding**
  - **Type**: Enum
    - **XML**
    - **Base64**: Base64 encoding
    - **Hex**: Hexadecimal encoding
    - **String**: Text encoding; UTF-8
    - **XML**: The WCF adapters create the BizTalk message body with the outer XML of the node selected by the body path expression in **InboundBodyPathExpression**.
  - **Description**: Specify the type of encoding that the WCF-Custom send adapter uses to decode for the node identified by the body path specified in **InboundBodyPathExpression**. This property is required if the **InboundBodyLocation** property is set to **UseBodyPath**. This property is valid only for solicit-response ports.

    Default value: **XML**

- **Property name**: **PropagateFaultMessage**
  - **Type**: Boolean
    - **True**: Route the message that fails outbound processing to a subscribing application (such as another receive port or orchestration schedule).
    - **False**: Suspend failed messages and generate a negative acknowledgment (NACK).
  - **Description**: Specify whether to route or suspend messages failed in outbound processing.

    This property is valid only for solicit-response ports.

    Default value: **True**

- **Property name**: **ReferencedBindings**
  - **Type**: XML Blob

    Example:

    ```xml
    <BindingConfiguration vt="8">
     <wsFederationHttpBinding>
      <binding name="sampleBinding">
       <security mode="Message">
        <message issuedKeyType="AsymmetricKey">
         <issuer address="https://www.contoso.com/samplests" binding="wsFederationHttpBinding" bindingConfiguration="contosoSTSBinding"/>
        </message>
       </security>
      </binding>
     </wsFederationHttpBinding>
    </BindingConfiguration>
    <ReferencedBindings vt="8">
     <bindings>
      <wsFederationHttpBinding>
       <binding name="contosoSTSBinding">
        <security mode="Message">
         <message negotiateServiceCredential="false">
          <issuer address="http://northwind.com/samplests" bindingConfiguration="northwindBinding" binding="wsHttpBinding">
          </issuer>
         </message>
        </security>
       </binding>
      </wsFederationHttpBinding>
      <wsHttpBinding>
       <binding name="northwindBinding">
        <security mode="Message">
         <message clientCredentialType="Certificate" />
        </security>
       </binding>
      </wsHttpBinding>
     </bindings>
    </ReferencedBindings>
    ```

    The **ReferencedBinding** property must not contain the binding configuration used in the **BindingConfiguration** property.

  - **Description**: Specify the binding configurations referenced by the **bindingConfiguration** attribute of the `<issuer>` element for the **wsFederationHttpBinding** and **customBinding**, which indicates the Security Token Service (STS) that issues security tokens. For more information about the `<issuer>` element, see [WCF configuration schema: `<issuer>`](/dotnet/framework/configure-apps/file-schema/wcf/issuer).

    The binding information including the `<issuer>` element for the **wsFederationHttpBinding** and **customBinding** can be configured through the **BindingConfiguration** property of the WCF-Custom and the WCF-CustomIsolated adapters. All of the referenced binding configurations for this property must be placed in the form of the `<bindings>` element.

     You cannot configure this property on the **Binding** tab in the transport properties dialog box. You can import and export this property through the **Import/Export** tab in the transport properties dialog box of the WCF-Custom and WCF-CustomIsolated adapters.
 
     The **bindingConfiguration** attribute of the `<issuer>` element must refer a valid binding name in this property.
 
     The `<issuer>` element in the referenced binding configurations can also refer to a different binding configuration in this property if this reference chain does not make a circular dependency.

    The default is an empty string.

## Configure a WCF-Custom Send Port with the BizTalk Administration Console

 You can set WCF-Custom send port adapter variables in the BizTalk Administration console. If properties are not set for the send port, the default values for the WCF-Custom send port configuration are used, as indicated in the previous table.

## Configure variables for a WCF-Custom send port

1. If you plan to use the WCF extensibility points such as the custom binding elements, custom behavior element, and custom channel components when configuring the WCF-Custom adapter, you must add the assemblies that implement the extensibility points and all of the dependent assemblies to the global assembly cache on both the BizTalk processing computer (runtime computer) and the administration computer. In addition, you must register the extension components to the machine.config file. For more information about how to use the WCF extensibility points with the WCF Custom adapter, see [How to Enable the WCF Extensibility Points with the WCF Adapters](../core/how-to-enable-the-wcf-extensibility-points-with-the-wcf-adapters.md).

2. In the BizTalk Administration console, create a new send port or double-click an existing send port to modify it. For more information, see [How to Create a Send Port](../core/how-to-create-a-send-port2.md). Configure all of the send port options and specify **WCF-Custom** for the **Type** option in the **Transport** section of the **General** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].

3. On the **General** tab, in the **Transport** section, click the **Configure** button next to **Type**.

4. In the **WCF-Custom Transport Properties** dialog box, on the **General** tab, configure the endpoint address, the service identity, and the **SOAPAction** header for the WCF-Custom send port. For more information about the **General** tab in the **WCF-Custom Transport Properties** dialog box, see the **WCF-Custom Transport Properties Dialog Box, Send, General** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].

5. In the **WCF-Custom Transport Properties** dialog box, on the **Binding** tab, configure different types of predefined or custom bindings for WCF. For more information about the **Binding** tab in the **WCF-Custom Transport Properties** dialog box, see the **WCF-Custom Transport Properties Dialog Box, Send, Binding** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].

6. In the **WCF-Custom Transport Properties** dialog box, on the **Behavior** tab, configure the endpoint behavior for this send port. An endpoint behavior is a set of the behavior extension elements that modify or extend service or client functionality. For more information about the **Behavior** tab in the **WCF-Custom Transport Properties** dialog box, see the **WCF-Custom Transport Properties Dialog Box, Send, Behavior** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].

7. In the **WCF-Custom Transport Properties** dialog box, on the **Credentials** tab, specify the credentials to be used when sending messages. For more information about the **Credentials** tab in the **WCF-Custom Transport Properties** dialog box see the **WCF-Custom Transport Properties Dialog Box, Send, Credentials** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].

8. In the **WCF-Custom Transport Properties** dialog box, on the **Messages** tab, specify the data selection for the SOAP **Body** element. For more information about the **Messages** tab in the **WCF-Custom Transport Properties** dialog box, see the **WCF-Custom Transport Properties Dialog Box, Send, Messages** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].

9. In the **WCF-Custom Transport Properties** dialog box, on the **Import/Export** tab, import and export the **Address (URI)** and **Endpoint Identity** properties on the **General** tab, binding information on the **Binding** tab, and endpoint behavior on the **Behavior** tab for this send port. For more information about the **Import/Export** tab in the **WCF-Custom Transport Properties** dialog box, see the **WCF-Custom Transport Properties Dialog Box, Send, Import-Export** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].

## Configure a WCF-Custom Send Port programmatically

 You can use the following format to set the properties:

```xml
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

```csharp
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
 [\<bindings\>](/dotnet/framework/configure-apps/file-schema/wcf/bindings)
 [\<behavior\> of \<endpointBehaviors\>](/dotnet/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors)
