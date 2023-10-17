---
description: "Learn more about: How to Use Message Context Properties"
title: "How to Use Message Context Properties"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Use Message Context Properties
System properties are mostly used internally by BizTalk Messaging Engine and its components. In general, changing the values set by the engine for those properties is not recommended, because it may affect the execution logic of the engine. However, there are a large number of properties that you can change.  
  
 The following table contains a list of message context properties that the Messaging Engine can promote. You can use these properties for creation of filter expressions on send ports and orchestrations in Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. For example,  
  
```  
PortName = MyMessage(BTS.ReceivePortName);  
MyFileName = MyMessage(BTS.ReceivedFileName);  
MySubject= MyMessage(POP3.Subject);  
```  
  
 A separate table lists additional properties that may be of use in some BizTalk applications that cannot be promoted.  
  
|Property|When and where it is promoted|Type|Description|  
|--------------|-----------------------------------|----------|-----------------|  
|BTS.AckFailureCategory|Promoted by the Messaging Engine before publishing an acknowledgement message into the MessageBox database.|xs:int|Identifies the **ErrorCategory**, which gives the place and reason for the suspension.|  
|BTS.AckFailureCode|Promoted by the Messaging Engine before publishing an acknowledgement message into the MessageBox database.|xs:string|Identifies the **ErrorCode**, which gives the place and reason for the suspension.|  
|BTS.AckID|Promoted by the Messaging Engine before publishing an acknowledgement message into the MessageBox database.|xs:string|Identifies the **MessageID** of the original message.|  
|BTS.AckInboundTransportLocation|Promoted by the Messaging Engine before publishing an acknowledgement message into the MessageBox database.|xs:string|Identifies the **InboundTransportLocation** from the original message.|  
|BTS.AckOutboundTransportLocation|Promoted by the Messaging Engine before publishing an acknowledgement message into the MessageBox database.|xs:string|Identifies the **OutboundTransportLocation** from the original message.|  
|BTS.AckOwnerID|Promoted by the Messaging Engine before publishing an acknowledgement message into the MessageBox database.|xs:string|Identifies the instance ID from original message.|  
|BTS.AckReceivePortID|Promoted by the Messaging Engine before publishing an acknowledgement message into the MessageBox database.|xs:string|Identifies the **ReceivePortID** from the original message.|  
|BTS.AckReceivePortName|Promoted by the Messaging Engine for the acknowledgement message.|xs:string|Identifies the **ReceivePortName** from the original message.|  
|BTS.AckSendPortID|Promoted by the Messaging Engine before publishing an acknowledgement message into the MessageBox database.|xs:string|Identifies the **SendPortID** from the original message.|  
|BTS.AckSendPortName|Promoted by the Messaging Engine before publishing an acknowledgement message into the MessageBox database.|xs:string|Identifies the **SendPortName** from the original message.|  
|BTS.AckType|Promoted by the Messaging Engine before publishing an acknowledgement message into the MessageBox database.|xs:string|Allows monitoring of acknowledgements and non-acknowledgements by an orchestration. The value will be ACK for an acknowledgment and NACK for a negative acknowledgment.|  
|BTS.ActionOnFailure|This property can be set by an adapter prior to calling IBTTTransportBatch::SubmitMessage() API to submit the message to BizTalk.|xs:int|Controls the behavior of the messaging engine when there is a failure in the receive pipeline. Typically the messaging engine suspends failed messages; however, certain adapters (like HTTP) would report the failure back to the client instead of suspending the message on a receive pipeline failure.<br /><br /> Valid values:<br /><br /> -   Default. If the property does not exist, the messaging engine will automatically try to suspend the message.<br />-   0. Indicates that the messaging engine should not automatically suspend the engine.<br /><br /> Other values are reserved for future use.|  
|BTS.CorrelationToken|If this property is set on the message context, it is promoted by the Messaging Engine. This property is set on a context implicitly when request-response adapter or an orchestration submits a request message into the MessageBox database.|xs:string|Enables routing of response to request-response ports.|  
|BTS.EpmRRCorrelationToken|Promoted by the Messaging Engine on request-response message execution. The property is promoted before messages are submitted into the MessageBox database.|xs:int|Used internally by the Messaging Engine. Specifies the Server Name, Process ID and a unique GUID for a request response stream of messages.|  
|BTS.InboundTransportLocation|Promoted by the Messaging Engine after receiving a message from a receive adapter and before publishing it into the MessageBox database.|xs:string|Specifies the location (URI) on which the message was received by the handler.|  
|BTS.InboundTransportType|Promoted by the Messaging Engine after receiving a message from a receive adapter and before publishing it into the MessageBox database.|xs:string|Specifies the type of adapter that received this message and submitted it into the server: FILE, HTTP, etc.|  
|BTS.InterchangeSequenceNumber|Pomoted by the Messaging Engine after receiving a message from the receive adapter and before publishing it into the MessageBox database.|xs:int|Indicates the sequence number of the document in the interchange. If the document is not part of an interchange that was disassembled into individual documents, then this value will be 1. The property can be read in an orchestration, a send pipeline and send adapter.|  
|BTS.IsDynamicSend|This property can be set on the message context. It will not be promoted, and it is only applied to Send operations.|xs:boolean|It is written to the message context by the Messaging Engine with a value of true when the send operation is on a Dynamic Send Port. If you would like to dynamically set properties for static send ports in the send pipelines, you will need to set this value to true.|  
|BTS.MessageDestination|This property can be set in the receive pipeline by a disassembler pipeline component when it returns a message from GetNext().|xs:string|Used primarily to support Recoverable Interchange Processing in disassemblers, this property controls whether a message is published to the message box or is suspended into the suspend queue. If a pipeline encounters a bad message in an interchange and wants to suspend the message and continue processing, it can do so by setting MessageDestination = SuspendQueue and return the message when the engine calls GetNext() on the disassembler.<br /><br /> Valid values:<br /><br /> -   Default. If the property does not exist, the message is assumed good and is published to the message box.<br />-   SuspendQueue. Directs the messaging engine to suspend the message. **Note:**  The suspended message will be the post-pipeline/mapping message and not the message submitted by the adapter (i.e. the wire message).|  
|BTS.MessageType|Promoted by the disassembler pipeline components during message parsing.|xs:string|Specifies the type of the message. The message type is defined as a concatenation of document schema namespace and document root node: http://<*MyNamespace*>#<*MyRoot*>.|  
|BTS.OutboundTransportLocation|If this property is set on the message context, it is promoted by the Messaging Engine. This property is set on a message context implicitly when an orchestration sends a message to a send port. This property can be also set explicitly in an orchestration or in a pipeline.|xs:string|Specifies the destination location URI where the message is sent. The URI may contain the adapter prefix, such as **http://**. The adapter prefix is used by the Messaging Engine to determine the type of adapter to use when sending the message. If both the adapter prefix and the **BTS.OutboundTransportType** property are set, the adapter type from **BTS.OutboundTransportType** always takes precedence over the adapter type determined from the prefix.<br /><br /> Valid values:<br /><br /> BizTalk Message Queuing: **DIRECT=**, **PRIVATE=**, and **PUBLIC=**<br /><br /> FILE: **file://**<br /><br /> FTP: **FTP://**<br /><br /> HTTP: **http://** and **https://**<br /><br /> SMTP: **mailto:**<br /><br /> SOAP: **SOAP://**<br /><br /> SQL: **SQL://**|  
|BTS.OutboundTransportType|If this property is set on the message context, it is promoted by the Messaging Engine. This property is set on a context implicitly when an orchestration sends a message to a send port. This property can also be set explicitly in an orchestration or in a pipeline.|xs:string|Specifies the type of adapter used to send the message. The available adapter types are **FILE**, **FTP**, **HTTP**, **SMTP**, **SOAP**, and **SQL**.<br /><br /> The values set on this property as well as adapter prefixes specified in the address are not case-sensitive.|  
|BTS.PropertiesToUpdate|An adapter sets this property when it needs to preserve some of the property values on a failed message that is being resubmitted or suspended.<br /><br /> This means that when the message gets resubmitted or resumed, it will have the specified properties set on the context.|xs:string|Contains an XML string with elements that represent property names, namespaces and values.|  
|BTS.ReceivePortID|Promoted by the Messaging Engine after receiving a message from a receive adapter and before publishing it into the MessageBox database.|xs:int|Identifies the receive port on which the message was received.|  
|BTS.ReceivePortName|Promoted by the Messaging Engine after receiving a message from a receive adapter and before publishing it into the MessageBox database.|xs:string|User-friendly name of the receive port on which the message was received.|  
|BTS.RouteDirectToTP|Promoted by the Messaging Engine on messages for loop back or request-response execution. The property is promoted before messages are submitted into the MessageBox database.|xs:boolean|Used internally by the Messaging Engine to enable loop back and request-response scenarios.|  
|BTS.SPGroupID|Promoted by the Messaging Engine when the message is sent to a send port from orchestration.|xs:string|Specifies the ID of the send port group.|  
|BTS.SPID|Promoted by the Messaging Engine when a message is sent to a send port from orchestration.|xs:string|Specifies the ID of the send port.|  
|BTS.SPName|Promoted by the Messaging Engine when publishing a response message from a Solicit-Response send port.|xs:string|Used for subscribing to the response messages from a Solicit-Response send port. The value is the name of the send port.|  
|BTS.SPTransportBackupID|Promoted by the Messaging Engine when a message is sent to a send port from an orchestration.|xs:string|Specifies the ID of the backup adapter in the send port.|  
|BTS.SPTransportID|Promoted by the Messaging Engine when a message is sent to a send port from an orchestration.|xs:string|Specifies the ID of the primary adapter in the send port.|  
|BTS.SuspendAsNonResumable|This property can be set by an adapter before calling SubmitMessage() or in an orchestration before sending a message to a send port. **Note:**  SubmitRequestMessage() will ignore this property; two-way messages are always suspended as non-resumable.|xs:boolean|Controls whether the Message Engine should suspend a message as non-resumable on message failure. Typically messages are suspended as resumable but there are cases when this is inappropriate -- for example, resuming a message for an ordered send or receive port would break message order.<br /><br /> Valid values:<br /><br /> -   False. Message is suspended as resumable (this is the default).<br />-   True. Message is suspended as non-resumable.|  
|BTS.SuspendMessageOnRoutingFailure|Promoted by the Messaging Engine after receiving a message from a receive adapter and before publishing it into the MessageBox database.|xs:boolean|Specifies behavior when a routing failure occurs with an incoming message.<br /><br /> Valid values:<br /><br /> -   Default / False. If the property does not exist or is set to False, the engine notifies the adapter of the error when a routing failure occurs.<br />-   True. The routing engine will suspend the message automatically when a routing failure occurs. **Note:**  The suspended message will be the post-pipeline/mapping message and not the message submitted by the adapter (i.e. the wire message).|  
  
 There are a number of other properties in this namespace that carry information that may be useful for some BizTalk applications.  
  
|Property|When and where it is promoted|Type|Description|  
|--------------|-----------------------------------|----------|-----------------|  
|BTS.AckDescription|Set by the Messaging Engine before publishing an acknowledgement message into the MessageBox database.|xs:string|Identifies the **ErrorDescription**, which gives the place and reason for the suspension.|  
|BTS.EncryptionCert|Not promotable.|xs:int|Identifies the thumbprint corresponding to the encryption certificate. Set this property in an orchestration or custom pipeline component placed before the MIME/SMIME Encoder pipeline component in a pipeline to perform response encryption on a request-response port that is receiving a signed and encrypted message.|  
|BTS.InterchangeID|Set by the Messaging Engine for each message that arrives on the server.|xs:string|Defines the unique ID that is used to group the documents that resulted from the same interchange message.|  
|BTS.Loopback|Set by an adapter when submitting the request message for loop back execution.|xs:boolean|Defines whether the message should be submitted into the server for a loop back execution. In loop back execution, the request message is published into the MessageBox database where it is routed directly to the receive adapter as a response.|  
|BTS.SignatureCertificate|Set by some adapters when submitting a message into the server. This property is used by the Party Resolution pipeline component.|xs:string|Identifies the thumbprint of the signing certificate that was used to sign the message received by BizTalk Server.|  
|BTS.SourcePartyID|Set by the Party Resolution pipeline component after the party has been identified for the incoming message.|xs:string|The ID of the BizTalk party.|  
|BTS.SSOTicket|If the receive adapter supports this property, it is set when publishing the message to a server.|xs:string|A ticket contains the encrypted domain and username of the current user, as well as the ticket expiration time. The ticket is used by SSO enabled adapters to get the credentials for the user when authenticating with destination endpoints.|  
|BTS.WindowsUser|Set by some adapters when submitting a message into the server. This property is used by the Party Resolution pipeline component.|xs:string|Specifies the account of a user on behalf of which the message is submitted into the server.|  
  
 For additional information about properties and property schemas associated with pipeline components and adapters, see the following:  
  
-   [File adapter property schema and properties](../core/file-adapter-property-schema-and-properties.md)
  
-   [FTP Adapter Property Schema and Properties](../core/ftp-adapter-property-schema-and-properties.md)  
  
-   [HTTP Adapter Property Schema and Properties](../core/http-adapter-property-schema-and-properties.md)  
  
-   [MSMQ Adapter Property Schema and Properties](../core/msmq-adapter-property-schema-and-properties.md)  
  
-   [SMTP Adapter Property Schema and Properties](../core/smtp-adapter-property-schema-and-properties.md)  
  
-   [SOAP Adapter Property Schema and Properties](../core/soap-adapter-property-schema-and-properties.md)  
  
-   [BizTalk Framework Schema and Properties](../core/biztalk-framework-schema-and-properties.md)  
  
-   [MQSeries Adapter Properties](../core/mqseries-adapter-properties.md)  
  
-   [POP3 Adapter Property Schema and Properties](../core/pop3-adapter-property-schema-and-properties.md)  
  
-   [Windows SharePoint Services Adapter Properties Reference](../core/windows-sharepoint-services-adapter-properties-reference.md)  
  
-   [MIME/SMIME Property Schema and Properties](../core/mime-smime-property-schema-and-properties.md)  
  
-   [XML and Flat File Property Schema and Properties](../core/xml-and-flat-file-property-schema-and-properties.md)  
  
## See Also  
 [About BizTalk Message Context Properties](../core/about-biztalk-message-context-properties.md)   
 [How to Use Expressions to Assign Values to Dynamic Ports](../core/how-to-use-expressions-to-assign-values-to-dynamic-ports.md)
