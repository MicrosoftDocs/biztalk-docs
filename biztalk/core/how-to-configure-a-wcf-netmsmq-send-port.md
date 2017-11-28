---
title: "How to Configure a WCF-NetMsmq Send Port | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 13f55e53-12af-473b-b73f-1c98edadfc28
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure a WCF-NetMsmq Send Port
You can configure a WCF-NetMsmq send port either programmatically or by using the BizTalk Administration console.  
  
## Configuration properties
  
 The BizTalk Explorer Object Model exposes an adapter-specific interface for send ports named **ITransportInfo** that has the **TransportTypeData** read/write property. This property accepts a WCF-NetMsmq send port configuration property bag in the form of a name-value pair of XML strings.  
  
 The **TransportTypeData** property of the **ITransportInfo** interface is not required. If it is not set, the adapter uses the default values for the WCF-NetMsmq send port configuration, as indicated in the following table.  
  
 The following table lists the configuration properties you can set in the BizTalk Explorer Object Model for WCF-NetMsmq send ports.  
  
|Property name|Type|Description|  
|-------------------|----------|-----------------|  
|**Identity**|XML Blob<br /><br /> Example :<br /><br /> &lt;identity&gt;<br /><br /> &lt;userPrincipalName value="username@contoso.com" /&gt;<br /><br /> &lt;/identity&gt;|Specify the identity of the service that this send port expects. These settings enable this send port to authenticate the service. In the handshake process between the client and service, the Windows Communication Foundation (WCF) infrastructure will ensure that the identity of the expected service matches the values of this element.<br /><br /> The default is an empty string.|  
|**StaticAction**|String|Specify the **SOAPAction** header field for outgoing messages. This property can also be set through the message context property **WCF.Action** in a pipeline or orchestration. You can specify this value in two different ways: the single action format and the action mapping format. If you set this property in the single action format- for example, http://contoso.com/Svc/Op1- the **SOAPAction** header for outgoing messages is always set to the value specified in this property.<br /><br /> If you set this property in the action mapping format, the outgoing **SOAPAction** header is determined by the **BTS.Operation** context property. For example, if this property is set to the following XML format and the **BTS.Operation** property is set to Op1, the WCF send adapter uses http://contoso.com/Svc/Op1 for the outgoing **SOAPAction** header.<br /><br /> \<BtsActionMapping\><br /><br /> \<Operation Name="Op1" Action="http://contoso.com/Svc/Op1" /\><br /><br /> \<Operation Name="Op2" Action="http://contoso.com/Svc/Op2" /\><br /><br /> \</BtsActionMapping\><br /><br /> If outgoing messages come from an orchestration port, orchestration instances dynamically set the **BTS.Operation** property with the operation name of the port. If outgoing messages are routed with content-based routing, you can set the **BTS.Operation** property in pipeline components.<br /><br /> The default is an empty string.|  
|**OpenTimeout**|**System.TimeSpan**|Specify a time span value that indicates the interval of time provided for a channel open operation to complete.<br /><br /> Default value: 00:01:00|  
|**SendTimeout**|**System.TimeSpan**|Specify a time span value that indicates the interval of time provided for a send operation to complete. If you use a solicit-response send port, this value specifies a time span for the whole interaction to complete, even if the service returns a large message.<br /><br /> Default value: 00:01:00|  
|**CloseTimeout**|**System.TimeSpan**|Specify a time span value that indicates the interval of time provided for a channel close operation to complete.<br /><br /> Default value: 00:01:00|  
|**EnableTransactional**|Boolean|Specify the type of the message queue for the destination service: transactional or nontransactional. If this property is set to **True**, each message processed by this send port is delivered only once, and the sender is notified of delivery failures. To send messages through transactional send ports, both the **durable** and **exactlyOnce** binding elements of the service must be set to **True**. If this property is set to **False**, messages are transferred without delivery assurance.<br /><br /> Default value: **True**|  
|**DeadLetterQueue**|Enum<br /><br /> -   **None** - No dead-letter queue is to be used.<br />-   **System** - Use the system-wide dead-letter queue.<br />-   **Custom** - Use a custom dead-letter queue.|Specify the dead-letter queue where messages that have failed to be delivered to the application will be transferred. For more information about the messages delivered to the dead-letter queue, see the **WCF-NetMsmq Transport Properties Dialog Box, Send, Binding** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].<br/><br/> **Note**:  The custom dead-letter queue is supported only in Message Queuing (MSMQ) 4.0, released with Windows Vista. <br /><br /> Default value: **System**|  
|**CustomDeadLetterQueue**|String|Specify the fully qualified URI with the **net.msmq** scheme for the location of the per-application dead-letter queue, where messages that have expired or that have failed transfer or delivery are placed. For example, net.msmq://localhost/deadLetterQueueName. The dead-letter queue is a queue on the queue manager of the sending application for expired messages that have failed to be delivered. This property is required if the **DeadLetterQueue** property is set to **Custom**.<br /><br /> The default is an empty string.|  
|**TimeToLive**|**System.TimeSpan**|Specify a time span for how long the messages are valid before they are expired and put into the dead-letter queue. This property is set to ensure that time-sensitive messages do not become stale before they are processed by this send port. A message in a queue that is not consumed by this send port within the time interval specified is said to be expired. Expired messages are sent to special queue called the dead-letter queue. The location of the dead-letter queue is set with the **DeadLetterQueue** property.<br /><br /> Default value: 1.00:00:00|  
|**UseSourceJournal**|Boolean|Specify whether copies of messages processed by this send port should be stored in the source journal queue.<br /><br /> Default value: **False**|  
|**SecurityMode**|Enum<br /><br /> -   **None**<br />-   **Message**<br />-   **Transport**<br />-   **Both**<br /><br /> For more information about the member names for the **SecurityMode** property, see the **Security mode** property in the **WCF-NetMsmq Transport Properties Dialog Box, Send, Security** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Specify the type of security that is used.<br /><br /> Default value: **Transport**|  
|**MsmqAuthenticationMode**|Enum<br /><br /> -   **None**<br />-   **WindowsDomain**<br />-   **Certificate**<br /><br /> For more information about the member names for the **MsmqAuthenticationMode** property, see the **MSMQ authentication mode** property in the **WCF-NetMsmq Transport Properties Dialog Box, Send, Security** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Specify how the message must be authenticated by the MSMQ transport.<br /><br /> Default value: **WindowsDomain**|  
|**MsmqProtectionLevel**|Enum<br /><br /> -   **None**: No protection.<br />-   **Sign**: Messages are signed.<br />-   **EncryptAndSign**: Messages are encrypted and signed. To use this protection level, you must enable **Active Directory Integration** for **MSMQ**.|Specify the way messages are secured at the level of the MSMQ transport.<br /><br /> Default value: **Sign**|  
|**MsmqSecureHashAlgorithm**|Enum<br /><br /> -   **MD5**<br />-   **SHA1**<br />-   **SHA25**<br />-   **SHA512**|Specify the hash algorithm to be used for computing the message digest. This property is not available if the **MsmqProtectionLevel** property is set to **None**.<br /><br /> Default value: **SHA1**|  
|**MsmqEncryptionAlgorithm**|Enum<br /><br /> -   **RC4Stream**<br />-   **AES**|Specify the algorithm to be used for message encryption on the wire when transferring messages between message queue managers. This property is available only if the **MsmqProtectionLevel** property is set to **EncryptAndSign**.<br /><br /> Default value: **RC4Stream**|  
|**MessageClientCredentialType**|Enum<br /><br /> -   **None**<br />-   **Windows**<br />-   **UserName**<br />-   **Certificate**<br /><br /> For more information about the member names for the **MessageClientCredentialType** property, see the **Message client credential type** property in the **WCF-NetMsmq Transport Properties Dialog Box, Send, Security** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Specify the type of credential to be used when performing client authentication using message-based security.<br /><br /> Default value: **Windows**|  
|**AlgorithmSuite**|Enum<br /><br /> For more information about the member names for the **AlgorithmSuite** property, see the **Algorithm suite** property in the **WCF-NetMsmq Transport Properties Dialog Box, Send, Security** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Specify the message encryption and key-wrap algorithms. These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.<br /><br /> Default value: **Basic256**|  
|**ClientCertificate**|String|Specify the thumbprint of the X.509 certificate for authenticating this send port to services. This property is required if the **ClientCredentialsType** property is set to **Certificate**. The certificate to be used for this property must be installed into the **My** store in the **Current User** location.<br /><br /> The default is an empty string.|  
|**ServiceCertificate**|String|Specify the thumbprint of the X.509 certificate for authenticating the service to which this send port sends messages. The certificate to be used for this property must be installed into the **Other People** store in the **Local Machine** location.<br /><br /> The default is an empty string.|  
|**AffiliateApplicationName**|String|Specify the affiliate application to use for Enterprise Single Sign-On (SSO).<br /><br /> The default is an empty string.|  
|**UseSSO**|Boolean|Specify whether to use Single Sign-On to retrieve client credentials for authentication with the destination server.<br /><br /> Default value: **False**|  
|**UserName**|String|Specify the user name to use for authentication with the destination server when the **UseSSO** property is set to **False**. You do not have to use the domain\user format for this property.<br /><br /> The default is an empty string.|  
|**Password**|String|Specify the password to use for authentication with the destination server when the **UseSSO** property is set to **False**.<br /><br /> The default is an empty string.|  
|**OutboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** - Use the BizTalk message body part to create the content of the SOAP **Body** element for an outgoing message.<br />-   **UseTemplate** - Use the template supplied in the **OutboundXMLTemplate** property to create the content of the SOAP **Body** element for an outgoing message.<br /><br /> For more information about how to use the **OutboundBodyLocation** property, see [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Specify the data selection for the SOAP **Body** element of outgoing WCF messages.<br /><br /> Default value: **UseBodyElement**|  
|**OutboundXMLTemplate**|String<br /><br /> For more information about how to use the **OutboundXMLTemplate** property, see [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Specify the XML-formatted template for the content of the SOAP **Body** element of an outgoing message. This property is required if the **OutboundBodyLocation** property is set to **UseTemplate**.<br /><br /> The default is an empty string.|  
  
## Configure a WCF-NetMsmq Send Port with the BizTalk Administration Console
  
 You can set WCF-NetMsmq send port adapter variables in the BizTalk Administration console. If properties are not set for the send port, the default values for the WCF-NetMsmq send port configuration are used, as indicated in the previous table.  
  
## Configure variables for a WCF-NetMsmq send port  
  
1.  In the BizTalk Administration console, create a new send port or double-click an existing send port to modify it. For more information, see [How to Create a Send Port](../core/how-to-create-a-send-port2.md). Configure all of the send port options and specify **WCF-NetMsmq** for the **Type** option in the **Transport** section of the **General** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
2.  On the **General** tab, in the **Transport** section, click the **Configure** button next to **Type**.  
  
3.  In the **WCF-NetMsmq Transport Properties** dialog box, on the **General** tab, configure the endpoint address, the service identity, and the **SOAPAction** header for the WCF-NetMsmq send port. For more information about the **General** tab in the **WCF-NetMsmq Transport Properties** dialog box, see the **WCF-NetMsmq Transport Properties Dialog Box, Send, General** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
4.  In the **WCF-NetMsmq Transport Properties** dialog box, on the **Binding** tab, configure the time-out and transaction properties and queue settings. For more information about the **Binding** tab in the **WCF-NetMsmq Transport Properties** dialog box, see the **WCF-NetMsmq Transport Properties Dialog Box, Send, Binding** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
5.  In the **WCF-NetMsmq Transport Properties** dialog box, on the **Security** tab, define the security capabilities of the WCF-NetMsmq send port. For more information about the **Security** tab in the **WCF-NetMsmq Transport Properties** dialog box, see the **WCF-NetMsmq Transport Properties Dialog Box, Send, Security** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
6.  In the **WCF-NetMsmq Transport Properties** dialog box, on the **Messages** tab, specify the data selection for the SOAP **Body** element. For more information about the **Messages** tab in the **WCF-NetMsmq Transport Properties** dialog box, see the **WCF-NetMsmq Transport Properties Dialog Box, Send, Messages** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
## Configure a WCF-NetMsmq Send Port Programmatically
  
 You can use the following format to set the properties:  
  
```  
<CustomProps>  
  <ServiceCertificate vt="8" />  
  <UseSSO vt="11">0</UseSSO>  
  <CloseTimeout vt="8">00:01:00</CloseTimeout>  
  <MessageClientCredentialType vt="8">Windows</MessageClientCredentialType>  
  <SendTimeout vt="8">00:01:00</SendTimeout>  
  <OutboundXmlTemplate vt="8"><bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="xml"/></OutboundXmlTemplate>  
  <MsmqProtectionLevel vt="8">Sign</MsmqProtectionLevel>  
  <OpenTimeout vt="8">00:01:00</OpenTimeout>  
  <UseSourceJournal vt="11">0</UseSourceJournal>  
  <AlgorithmSuite vt="8">Basic256</AlgorithmSuite>  
  <SecurityMode vt="8">Transport</SecurityMode>  
  <CustomDeadLetterQueue vt="8" />  
  <ClientCertificate vt="8" />  
  <MsmqEncryptionAlgorithm vt="8">RC4Stream</MsmqEncryptionAlgorithm>  
  <StaticAction vt="8">http://www.northwindtraders.com/Service/Operation</StaticAction>  
  <MsmqSecureHashAlgorithm vt="8">Sha1</MsmqSecureHashAlgorithm>  
  <EnableTransaction vt="11">-1</EnableTransaction>  
  <TimeToLive vt="8">1.00:00:00</TimeToLive>  
  <MsmqAuthenticationMode vt="8">WindowsDomain</MsmqAuthenticationMode>  
  <DeadLetterQueue vt="8">System</DeadLetterQueue>  
  <OutboundBodyLocation vt="8">UseBodyElement</OutboundBodyLocation>  
</CustomProps>  
  
```  
  
 The following code fragment illustrates creating a WCF-NetMsmq send port:  
  
```  
// Use BizTalk Explorer object model to create new WCF-NetMsmq send port.  
string server = System.Environment.MachineName;  
string database = "BizTalkMgmtDb";  
string connectionString = string.Format("Server={0};Database={1};Integrated Security=true", server, database);  
string transportConfigData = @"<CustomProps>  
                                 <StaticAction vt=""8"">http://www.northwindtraders.com/Service/Operation</StaticAction>  
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
sendPort.PrimaryTransport.TransportType = explorer.ProtocolTypes["WCF-NetMsmq"];  
sendPort.PrimaryTransport.Address = "net.msmq://mycomputer/private/samplequeue";  
sendPort.PrimaryTransport.TransportTypeData = transportConfigData; // propertyData; // need to change  
sendPort.SendPipeline = explorer.Pipelines["Microsoft.BizTalk.DefaultPipelines.PassThruTransmit"];  
// Save  
explorer.SaveChanges();  
```  
  
## See Also  
 [WCF Adapters Property Schema and Properties](../core/wcf-adapters-property-schema-and-properties.md)   
 [Installing Certificates for the WCF Adapters](../core/installing-certificates-for-the-wcf-adapters.md)   
 [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md)   
 [Configuring the WCF-NetMsmq Adapter](../core/configuring-the-wcf-netmsmq-adapter.md)   
 [Configuring Dynamic Send Ports Using WCF Adapters Context Properties](../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)