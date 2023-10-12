---
description: "Learn more about: How to Configure a WCF-NetMsmq Receive Location"
title: "How to Configure a WCF-NetMsmq Receive Location"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Configure a WCF-NetMsmq Receive Location
You can configure a WCF-NetMsmq receive location either programmatically or by using the BizTalk Administration console.

## Configuration properties

 The BizTalk Explorer Object Model enables you to create and configure receive locations programmatically. The BizTalk Explorer Object Model exposes the**IReceiveLocation** receive location configuration interface that has a **TransportTypeData** read/write property. This property accepts a WCF-NetMsmq receive location configuration property bag in the form of a name-value pair of XML strings. To set this property in the BizTalk Explorer Object Model, you must set the **InboundTransportLocation** property of the **IReceiveLocation** interface.

 The **TransportTypeData** property of the **IReceiveLocation** interface does not have to be set. If it is not set, the WCF-NetMsmq adapter uses the default values for the WCF-NetMsmq receive location configuration as indicated in the following table.

 The following table lists the configuration properties that you can set in the BizTalk Explorer Object Model for the WCF-NetMsmq receive location.

| Property name | Type  |  Description  |
|---|---|---|
|            **Identity**            | XML Blob<br /><br /> Example:<br /><br /> &lt;identity&gt;<br /><br /> &lt;userPrincipalName value="username@contoso.com" /&gt;<br /><br /> &lt;/identity&gt; |  Specify the identity of the service that this receive location provides. The values that can be specified for the **Identity** property differ according to the security configuration. These settings enable the client to authenticate this receive location. In the handshake process between the client and service, the Windows Communication Foundation (WCF) infrastructure will ensure that the identity of the expected service matches the values of this element.<br /><br /> The default is an empty string.                                                                                          |
|          **OpenTimeout**           |  **System.TimeSpan**  |  Specify a time span value that indicates the interval of time provided for a channel open operation to complete.<br /><br /> Default value: 00:01:00  |
|          **SendTimeout**           | **System.TimeSpan**  | Specify a time span value that indicates the interval of time provided for a send operation to complete.<br /><br /> Default value: 00:01:00  |
|          **CloseTimeout**          | **System.TimeSpan**  | Specify a time span value that indicates the interval of time provided for a channel close operation to complete.<br /><br /> Default value: 00:01:00  |
|     **MaxReceivedMessageSize**     |  Integer  | Specify the maximum size, in bytes, for a message (including headers) that can be received on the wire. The size of the messages is bounded by the amount of memory allocated for each message. You can use this property to limit exposure to denial of service (DoS) attacks.<br /><br /> Default value: 65536 |
|       **EnableTransaction**        |  Boolean |  Specify the type of message queue: transactional or nontransactional. If this property is selected, each message is delivered only once, and the sender is notified of delivery failures. To send messages through transactional send ports, both the **durable** and **exactlyOnce** binding elements of the client must be set to **True**. If this property is cleared, messages are transferred without delivery assurance. **Note:**  If you use a transactional queue under this receive location, this property must be selected. <br /><br /> Default value: **False**  |
|       **OrderedProcessing**        |  Boolean   | Specify whether to process messages serially. When this property is selected, this receive location accommodates ordered message delivery when used in conjunction with a BizTalk messaging or orchestration send port that has the **Ordered Delivery** option set to `True`. You can select this only when the **EnableTransaction** property is set to **True**.<br /><br /> For more information about the **Ordered Delivery** option, see the appropriate topics in See Also.<br /><br /> When this property is set to **True**, the WCF-NetMsmq receive location optimizes resource usage when handling large messages by making the adapter single-threaded.<br /><br /> Default value: **False** |
|       **MaxConcurrentCalls**       | Integer  |  Specify the number of concurrent calls to a single service instance. Calls in excess of the limit are queued. The range of this property is from 0 to **Int32.MaxValue**.<br /><br /> Default value: 200  |
|          **SecurityMode**          |  Enum<br /><br /> -   **None**<br />-   **Message**<br />-   **Transport**<br />-   **Both**<br /><br /> For more information about the member names for the **SecurityMode** property, see the **Security mode** property in the **WCF-NetMsmq Transport Properties Dialog Box, Receive, Security** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]. |  Specify the type of security that is used.<br /><br /> Default value: **Transport**  |
|     **MsmqAuthenticationMode**     |  Enum<br /><br /> -   **None**<br />-   **WindowsDomain**<br />-   **Certificate**<br /><br /> For more information about the member names for the **MsmqAuthenticationMode** property, see the **MSMQ authentication mode** property in the **WCF-NetMsmq Transport Properties Dialog Box, Receive, Security** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  |  Specify how the message must be authenticated by the MSMQ transport.<br /><br /> Default value: **WindowsDomain**  |
|      **MsmqProtectionLevel**       |  Enum<br /><br /> -   **None**: No protection.<br />-   **Sign**: Messages are signed.<br />-   **EncryptAndSign**: Messages are encrypted and signed. To use this protection level, you must enable **Active Directory Integration** for **MSMQ**. |  Specify the way messages are secured at the level of the MSMQ transport. Encryption ensures message integrity, while sign and encrypt ensures both message integrity and non-repudiation.<br /><br /> Default value: **Sign**   |
|    **MsmqSecureHashAlgorithm**     |  Enum<br /><br /> -   **MD5**<br />-   **SHA1**<br />-   **SHA25**<br />-   **SHA512**  |  Specify the hash algorithm to be used for computing the message digest. This property is not available if the **MsmqProtectionLevel** property is set to **None**.<br /><br /> Default value: **SHA1**  |
|    **MsmqEncryptionAlgorithm**     |  Enum<br /><br /> -   **RC4Stream**<br />-   **AES**  |   Specify the algorithm to be used for message encryption on the wire when transferring messages between message queue managers. This property is available only if the **MsmqProtectionLevel** property is set to **EncryptAndSign**.<br /><br /> Default value: **RC4Stream**  |
|  **MessageClientCredentialType**   |  Enum<br /><br /> -   **None**<br />-   **Windows**<br />-   **UserName**<br />-   **Certificate**<br /><br /> For more information about the member names for the **MessageClientCredentialType** property, see the **Message client credential type** property in the **WCF-NetMsmq Transport Properties Dialog Box, Receive, Security** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  | Specify the type of credential to be used when performing client authentication using message-based security.<br /><br /> Default value: **Windows**   |
|         **AlgorithmSuite**         |  Enum<br /><br /> For more information about the member names for the **AlgorithmSuite** property, see the **Algorithm suite** property in the **WCF-NetMsmq Transport Properties Dialog Box, Receive, Security** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  |  Specify the message encryption and key-wrap algorithms. These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.<br /><br /> Default value: **Basic256**   |
|       **ServiceCertificate**       |  String  |  Specify the thumbprint of the X.509 certificate for this receive location that the clients use to authenticate the service. The certificate to be used for this property must be installed into the **My** store in the **Current User** location. **Note:**  You must install the service certificate into the **Current User** location of the user account for the receive handler hosting this receive location. <br /><br /> The default is an empty string.  |
|      **InboundBodyLocation**       | Enum<br /><br /> -   **UseBodyElement** - Use the content of the SOAP **Body** element of an incoming message to create the BizTalk message body part. If the **Body** element has more than one child element, only the first element becomes the BizTalk message body part.<br />-   **UseEnvelope** - Create the BizTalk message body part from the entire SOAP **Envelope** of an incoming message.<br />-   **UseBodyPath** - Use the body path expression in the **InboundBodyPathExpression** property to create the BizTalk message body part. The body path expression is evaluated against the immediate child element of the SOAP **Body** element of an incoming message. This property is valid only for solicit-response ports.<br /><br /> For more information about how to use the **InboundBodyLocation** property, see [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md). |  Specify the data selection for the SOAP **Body** element of incoming WCF messages.<br /><br /> Default value: **UseBodyElement**  |
|   **InboundBodyPathExpression**    |  String<br /><br /> For more information about how to use the **InboundBodyPathExpression** property, see [WCF Adapters Property Schema and Properties](../core/wcf-adapters-property-schema-and-properties.md).  |  Specify the body path expression to identify a specific part of an incoming message used to create the BizTalk message body part. This body path expression is evaluated against the immediate child element of the SOAP **Body** node of an incoming message. If this body path expression returns more than one node, only the first node is chosen for the BizTalk message body part. This property is required if the **InboundBodyLocation** property is set to **UseBodyPath**.<br /><br /> The default is an empty string.                                                                                     |
|      **InboundNodeEncoding**       |  Enum<br /><br /> -   **Base64** - Base64 encoding.<br />-   **Hex** - Hexadecimal encoding.<br />-   **String** - Text encoding - UTF-8.<br />-   **XML** - The WCF adapters create the BizTalk message body with the outer XML of the node selected by the body path expression in **InboundBodyPathExpression**. |  Specify the type of encoding that the WCF-NetMsmq receive adapter uses to decode the node identified by the body path expression specified in **InboundBodyPathExpression**. This property is required if the **InboundBodyLocation** property is set to **UseBodyPath**.<br /><br /> Default value: **XML**  |
|    **DisableLocationOnFailure**    |  Boolean |   Specify whether to disable the receive location that fails inbound processing due to a receive pipeline failure or a routing failure.<br /><br /> Default: **False** |
|    **SuspendMessageOnFailure**     |  Boolean |   Specify whether to suspend the request message that fails inbound processing due to a receive pipeline failure or a routing failure.<br /><br /> Default value: **True**  |
| **IncludeExceptionDetailInFaults** |  Boolean  | Specify whether to include managed exception information in the detail of SOAP faults returned to the client for debugging purposes.<br /><br /> Default: **False**  |

## Configure a WCF-NetMsmq Receive Location with the BizTalk Administration Console

 You can set WCF-NetMsmq receive location adapter variables in the BizTalk Administration console. If properties are not set in the receive location, the default receive handler values set in the BizTalk Administration console are used.

> [!NOTE]
>  Before completing the following procedure you must have already added a receive port. For more information, see [How to Create a Receive Port](../core/how-to-create-a-receive-port.md).

> [!NOTE]
>  The binding configurations of WCF clients and WCF-NetMsmq receive locations must match. If they do not match, the WCF-NetMsmq receive locations can lose incoming messages.

## Configure variables for a WCF-NetMsmq receive location

1. In the BizTalk Administration console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the application you want to create a receive location in.

2. In the BizTalk Administration console, in the left pane, click the **Receive Port** node. Then in the right pane, right-click the receive port that is associated with an existing receive location or that you want to associate with a new receive location, and then click **Properties**.

3. In the **Receive Port Properties** dialog box, in the left pane, select **Receive Locations**, and then in the right pane, double-click an existing receive location or click **New**to create a new receive location.

4. In the **Receive Location Properties** dialog box, in the **Transport** section next to **Type**, select **WCF-NetMsmq** from the drop-down list, and then click **Configure**.

5. In the **WCF-NetMsmq Transport Properties** dialog box, on the **General** tab, configure the endpoint address and the service identity for the WCF-NetMsmq receive location. For more information about the **General** tab in the **WCF-NetMsmq Transport Properties** dialog box, see the **WCF-NetMsmq Transport Properties Dialog Box, Receive, General** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].

6. In the **WCF-NetMsmq Transport Properties** dialog box, on the **Binding** tab, configure the time-out and transaction properties. For more information about the **Binding** tab in the **WCF-NetMsmq Transport Properties** dialog box, see the **WCF-NetMsmq Transport Properties Dialog Box, Receive, Binding** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].

7. In the **WCF-NetMsmq Transport Properties** dialog box, on the **Security** tab, define the security capabilities of the WCF-NetMsmq receive location. For more information about the **Security** tab in the **WCF-NetMsmq Transport Properties** dialog box, see the **WCF-NetMsmq Transport Properties Dialog Box, Receive, Security** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].

8. In the **WCF-NetMsmq Transport Properties** dialog box, on the **Messages** tab, specify the data selection for the SOAP **Body** element. For more information about the **Messages** tab in the **WCF-NetMsmq Transport Properties** dialog box, see the **WCF-NetMsmq Transport Properties Dialog Box, Receive, Messages** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].

## Configure a WCF-NetMsmq Receive Location Programmatically

 You can use the following format to set the properties:

```xml
<CustomProps>
  <ServiceCertificate vt="8" />
  <InboundBodyLocation vt="8">UseBodyElement</InboundBodyLocation>
  <InboundBodyPathExpression vt="8" />
  <MessageClientCredentialType vt="8">Windows</MessageClientCredentialType>
  <SendTimeout vt="8">00:01:00</SendTimeout>
  <IncludeExceptionDetailInFaults vt="11">0</IncludeExceptionDetailInFaults>
  <OpenTimeout vt="8">00:01:00</OpenTimeout>
  <AlgorithmSuite vt="8">Basic256</AlgorithmSuite>
  <MaxConcurrentCalls vt="3">16</MaxConcurrentCalls>
  <SecurityMode vt="8">Transport</SecurityMode>
  <OrderedProcessing vt="11">0</OrderedProcessing>
  <CloseTimeout vt="8">00:01:00</CloseTimeout>
  <MsmqEncryptionAlgorithm vt="8">RC4Stream</MsmqEncryptionAlgorithm>
  <MaxReceivedMessageSize vt="3">2097152</MaxReceivedMessageSize>
  <MsmqProtectionLevel vt="8">Sign</MsmqProtectionLevel>
  <DisableLocationOnFailure vt="11">0</DisableLocationOnFailure>
  <MsmqSecureHashAlgorithm vt="8">Sha1</MsmqSecureHashAlgorithm>
  <SuspendMessageOnFailure vt="11">-1</SuspendMessageOnFailure>
  <EnableTransaction vt="11">-1</EnableTransaction>
  <InboundNodeEncoding vt="8">Xml</InboundNodeEncoding>
  <MsmqAuthenticationMode vt="8">WindowsDomain</MsmqAuthenticationMode>
</CustomProps>

```

 The following code fragment illustrates creating a WCF-NetMsmq receive location:

```csharp
// Use BizTalk Explorer object model to create new WCF-NetMsmq receive location
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
IReceiveLocation receiveLocation = receivePort.AddNewReceiveLocation();
receiveLocation.Name = "SampleReceiveLocation";
// Find a receive handler for WCF-NetMsmq
int i = 0;
for(i=0; i < explorer.ReceiveHandlers.Count; ++i)
{
    if("WCF-NetMsmq" == explorer.ReceiveHandlers[i].TransportType.Name)
        break;
}
receiveLocation.ReceiveHandler = explorer.ReceiveHandlers[i];
receiveLocation.Address = "net.msmq://mycomputer/private/sampleQueue";
receiveLocation.ReceivePipeline = explorer.Pipelines["Microsoft.BizTalk.DefaultPipelines.PassThruReceive"];
receiveLocation.TransportType = explorer.ProtocolTypes["WCF-NetMsmq"];
receiveLocation.TransportTypeData = transportConfigData;
// Save
explorer.SaveChanges();
```

## See Also
 [Publishing Service Metadata for the WCF Receive Adapters](../core/publishing-service-metadata-for-the-wcf-receive-adapters.md)
 [Managing BizTalk Hosts and Host Instances](../core/managing-biztalk-hosts-and-host-instances.md)
 [How to Change Service Accounts and Passwords](../core/how-to-change-service-accounts-and-passwords.md)
 [Installing Certificates for the WCF Adapters](../core/installing-certificates-for-the-wcf-adapters.md)
 [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md)
 [Configuring the WCF-NetMsmq Adapter](../core/configuring-the-wcf-netmsmq-adapter.md)
 [Ordered Delivery of Messages](../core/ordered-delivery-of-messages.md)
 [Sending and Retrieving Messages within a Transaction](/previous-versions/windows/desktop/msmq/ms702030(v=vs.85))
 [Message Queuing and Active Directory](/previous-versions/windows/it-pro/windows-server-2003/cc736601(v=ws.10))
 [Public and private queues](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753440(v=ws.10))
