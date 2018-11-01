---
title: Message Context Properties1
TOCTitle: Message Context Properties
ms:assetid: fce413a0-5b61-48b2-8a5d-c1cf496df616
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa562116(v=BTS.80)
ms:contentKeyID: 51533723
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Message Context Properties

 

System properties are mostly used internally by BizTalk Messaging Engine and its components. In general, changing the values set by the engine for those properties is not recommended, because it may affect the execution logic of the engine. However, there are a large number of properties that you can change.

The following table contains a list of message context properties that the Messaging Engine can promote. You can use these properties for creation of filter expressions on send ports and orchestrations in Microsoft BizTalk Server. A separate table lists additional properties that may be of use in some BizTalk applications that cannot be promoted.

For additional information about properties and property schemas associated with pipeline components and adapters, see the following:

  - [File Adapter Property Schema and Properties](https://msdn.microsoft.com/en-us/library/aa547908\(v=bts.80\))

  - [FTP Adapter Property Schema and Properties](https://msdn.microsoft.com/en-us/library/aa560564\(v=bts.80\))

  - [HTTP Adapter Property Schema and Properties](https://msdn.microsoft.com/en-us/library/aa547980\(v=bts.80\))

  - [MSMQ Adapter Property Schema and Properties](https://msdn.microsoft.com/en-us/library/aa577593\(v=bts.80\))

  - [SMTP Adapter Property Schema and Properties](https://msdn.microsoft.com/en-us/library/aa560686\(v=bts.80\))

  - [SOAP Adapter Property Schema and Properties](https://msdn.microsoft.com/en-us/library/aa578208\(v=bts.80\))

  - [BizTalk Framework Schema and Properties](https://msdn.microsoft.com/en-us/library/aa561250\(v=bts.80\))

  - [MQSeries Adapter Properties](https://msdn.microsoft.com/en-us/library/aa547870\(v=bts.80\))

  - [POP3 Adapter Property Schema and Properties](https://msdn.microsoft.com/en-us/library/aa560937\(v=bts.80\))

  - [Windows SharePoint Services Adapter Properties Reference](https://msdn.microsoft.com/en-us/library/aa547920\(v=bts.80\))

  - [MIME/SMIME Property Schema and Properties](https://msdn.microsoft.com/en-us/library/aa559271\(v=bts.80\))

  - [XML and Flat File Property Schema and Properties](https://msdn.microsoft.com/en-us/library/aa559096\(v=bts.80\))

  - [WCF Adapters Property Schema and Properties](https://msdn.microsoft.com/en-us/library/bb245991\(v=bts.80\))

  - [AS2 Context Properties](https://msdn.microsoft.com/en-us/library/bb226483\(v=bts.80\))

  - [EDI Context Properties](https://msdn.microsoft.com/en-us/library/bb226554\(v=bts.80\))

<table>
<thead>
<tr class="header">
<th>Property</th>
<th>When and where it is promoted</th>
<th>Type</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>BTS.AckFailureCategory</td>
<td>Promoted by the Messaging Engine before publishing an acknowledgement message into the MessageBox database.</td>
<td>xs:int</td>
<td>Identifies the <strong>ErrorCategory</strong>, which gives the place and reason for the suspension.</td>
</tr>
<tr class="even">
<td>BTS.AckFailureCode</td>
<td>Promoted by the Messaging Engine before publishing an acknowledgement message into the MessageBox database.</td>
<td>xs:string</td>
<td>Identifies the <strong>ErrorCode</strong>, which gives the place and reason for the suspension.</td>
</tr>
<tr class="odd">
<td>BTS.AckID</td>
<td>Promoted by the Messaging Engine before publishing an acknowledgement message into the MessageBox database.</td>
<td>xs:string</td>
<td>Identifies the <strong>MessageID</strong> of the original message.</td>
</tr>
<tr class="even">
<td>BTS.AckInboundTransportLocation</td>
<td>Promoted by the Messaging Engine before publishing an acknowledgement message into the MessageBox database.</td>
<td>xs:string</td>
<td>Identifies the <strong>InboundTransportLocation</strong> from the original message.</td>
</tr>
<tr class="odd">
<td>BTS.AckOutboundTransportLocation</td>
<td>Promoted by the Messaging Engine before publishing an acknowledgement message into the MessageBox database.</td>
<td>xs:string</td>
<td>Identifies the <strong>OutboundTransportLocation</strong> from the original message.</td>
</tr>
<tr class="even">
<td>BTS.AckOwnerID</td>
<td>Promoted by the Messaging Engine before publishing an acknowledgement message into the MessageBox database.</td>
<td>xs:string</td>
<td>Identifies the instance ID from original message.</td>
</tr>
<tr class="odd">
<td>BTS.AckReceivePortID</td>
<td>Promoted by the Messaging Engine before publishing an acknowledgement message into the MessageBox database.</td>
<td>xs:string</td>
<td>Identifies the <strong>ReceivePortID</strong> from the original message.</td>
</tr>
<tr class="even">
<td>BTS.AckReceivePortName</td>
<td>Promoted by the Messaging Engine for the acknowledgement message.</td>
<td>xs:string</td>
<td>Identifies the <strong>ReceivePortName</strong> from the original message.</td>
</tr>
<tr class="odd">
<td>BTS.AckSendPortID</td>
<td>Promoted by the Messaging Engine before publishing an acknowledgement message into the MessageBox database.</td>
<td>xs:string</td>
<td>Identifies the <strong>SendPortID</strong> from the original message.</td>
</tr>
<tr class="even">
<td>BTS.AckSendPortName</td>
<td>Promoted by the Messaging Engine before publishing an acknowledgement message into the MessageBox database.</td>
<td>xs:string</td>
<td>Identifies the <strong>SendPortName</strong> from the original message.</td>
</tr>
<tr class="odd">
<td>BTS.AckType</td>
<td>Promoted by the Messaging Engine before publishing an acknowledgement message into the MessageBox database.</td>
<td>xs:string</td>
<td>Allows monitoring of acknowledgements and non-acknowledgements by an orchestration. The value will be ACK for an acknowledgment and NACK for a negative acknowledgment.</td>
</tr>
<tr class="even">
<td>BTS.ActionOnFailure</td>
<td>This property can be set by an adapter prior to calling IBTTTransportBatch::SubmitMessage() API to submit the message to BizTalk.</td>
<td>xs:int</td>
<td>Controls the behavior of the messaging engine when there is a failure in the receive pipeline. Typically the messaging engine suspends failed messages; however, certain adapters (like HTTP) would report the failure back to the client instead of suspending the message on a receive pipeline failure.<br />
<br />
Valid values:<br />
<br />
- Default. If the property does not exist, the messaging engine will automatically try to suspend the message.<br />
<br />
- 0. Indicates that the messaging engine should not automatically suspend the engine.<br />
<br />
Other values are reserved for future use.</td>
</tr>
<tr class="odd">
<td>BTS.CorrelationToken</td>
<td>If this property is set on the message context, it is promoted by the Messaging Engine. This property is set on a context implicitly when request-response adapter or an orchestration submits a request message into the MessageBox database.</td>
<td>xs:string</td>
<td>Enables routing of response to request-response ports.</td>
</tr>
<tr class="even">
<td>BTS.EpmRRCorrelationToken</td>
<td>Promoted by the Messaging Engine on request-response message execution. The property is promoted before messages are submitted into the MessageBox database.</td>
<td>xs:int</td>
<td>Used internally by the Messaging Engine. Specifies the Server Name, Process ID and a unique GUID for a request response stream of messages.</td>
</tr>
<tr class="odd">
<td>BTS.InboundTransportLocation</td>
<td>Promoted by the Messaging Engine after receiving a message from a receive adapter and before publishing it into the MessageBox database.</td>
<td>xs:string</td>
<td>Specifies the location (URI) on which the message was received by the handler.</td>
</tr>
<tr class="even">
<td>BTS.InboundTransportType</td>
<td>Promoted by the Messaging Engine after receiving a message from a receive adapter and before publishing it into the MessageBox database.</td>
<td>xs:string</td>
<td>Specifies the type of adapter that received this message and submitted it into the server: FILE, HTTP, etc.</td>
</tr>
<tr class="odd">
<td>BTS.InterchangeSequenceNumber</td>
<td>Pomoted by the Messaging Engine after receiving a message from the receive adapter and before publishing it into the MessageBox database.</td>
<td>xs:int</td>
<td>Indicates the sequence number of the document in the interchange. If the document is not part of an interchange that was disassembled into individual documents, then this value will be 1. The property can be read in an orchestration, a send pipeline and send adapter.</td>
</tr>
<tr class="even">
<td>BTS.MessageDestination</td>
<td>This property can be set in the receive pipeline by a disassembler pipeline component when it returns a message from GetNext().</td>
<td>xs:string</td>
<td>Used primarily to support Recoverable Interchange Processing in disassemblers, this property controls whether a message is published to the message box or is suspended into the suspend queue. If a pipeline encounters a bad message in an interchange and wants to suspend the message and continue processing, it can do so by setting MessageDestination = SuspendQueue and return the message when the engine calls GetNext() on the disassembler.<br />
<br />
Valid values:<br />
<br />
- Default. If the property does not exist, the message is assumed good and is published to the message box.<br />
<br />
- SuspendQueue. Directs the messaging engine to suspend the message.<br />
<br />
 <strong>Note</strong> The suspended message will be the post-pipeline/mapping message and not the message submitted by the adapter (i.e. the wire message).</td>
</tr>
<tr class="odd">
<td>BTS.MessageType</td>
<td>Promoted by the disassembler pipeline components during message parsing.</td>
<td>xs:string</td>
<td>Specifies the type of the message. The message type is defined as a concatenation of document schema namespace and document root node: http://&lt;<em>MyNamespace</em>&gt;#&lt;<em>MyRoot</em>&gt;.</td>
</tr>
<tr class="even">
<td>BTS.OutboundTransportLocation</td>
<td>If this property is set on the message context, it is promoted by the Messaging Engine. This property is set on a message context implicitly when an orchestration sends a message to a send port. This property can be also set explicitly in an orchestration or in a pipeline.</td>
<td>xs:string</td>
<td>Specifies the destination location URI where the message is sent. The URI may contain the adapter prefix, such as <strong>http://</strong>. The adapter prefix is used by the Messaging Engine to determine the type of adapter to use when sending the message. If both the adapter prefix and the <strong>BTS.OutboundTransportType</strong> property are set, the adapter type from <strong>BTS.OutboundTransportType</strong> always takes precedence over the adapter type determined from the prefix.<br />
<br />
Valid values:<br />
<br />
BizTalk Message Queuing: <strong>DIRECT=</strong>, <strong>PRIVATE=</strong>, and <strong>PUBLIC=</strong><br />
<br />
FILE: <strong>file://</strong><br />
<br />
FTP: <strong>FTP://</strong><br />
<br />
HTTP: <strong>http://</strong> and <strong>https://</strong><br />
<br />
SMTP: <strong>mailto:</strong><br />
<br />
SOAP: <strong>SOAP://</strong><br />
<br />
SQL: <strong>SQL://</strong></td>
</tr>
<tr class="odd">
<td>BTS.OutboundTransportType</td>
<td>If this property is set on the message context, it is promoted by the Messaging Engine. This property is set on a context implicitly when an orchestration sends a message to a send port. This property can also be set explicitly in an orchestration or in a pipeline.</td>
<td>xs:string</td>
<td>Specifies the type of adapter used to send the message. The available adapter types are <strong>FILE</strong>, <strong>FTP</strong>, <strong>HTTP</strong>, <strong>SMTP</strong>, <strong>SOAP</strong>, and <strong>SQL</strong>.<br />
<br />
The values set on this property as well as adapter prefixes specified in the address are not case-sensitive.</td>
</tr>
<tr class="even">
<td>BTS.PropertiesToUpdate</td>
<td>An adapter sets this property when it needs to preserve some of the property values on a failed message that is being resubmitted or suspended.<br />
<br />
This means that when the message gets resubmitted or resumed, it will have the specified properties set on the context.</td>
<td>xs:string</td>
<td>Contains an XML string with elements that represent property names, namespaces and values.</td>
</tr>
<tr class="odd">
<td>BTS.ReceiveLocationName</td>
<td>Written to the message context by the Messaging Engine after receiving a message from a receive adapter and before publishing it into the MessageBox database.</td>
<td>xs:string</td>
<td>User-friendly name of the receive location on which the message was received.</td>
</tr>
<tr class="even">
<td>BTS.ReceivePortID</td>
<td>Promoted by the Messaging Engine after receiving a message from a receive adapter and before publishing it into the MessageBox database.</td>
<td>xs:int</td>
<td>Identifies the receive port on which the message was received.</td>
</tr>
<tr class="odd">
<td>BTS.ReceivePortName</td>
<td>Promoted by the Messaging Engine after receiving a message from a receive adapter and before publishing it into the MessageBox database.</td>
<td>xs:string</td>
<td>User-friendly name of the receive port on which the message was received.</td>
</tr>
<tr class="even">
<td>BTS.RouteDirectToTP</td>
<td>Promoted by the Messaging Engine on messages for loop back or request-response execution. The property is promoted before messages are submitted into the MessageBox database.</td>
<td>xs:boolean</td>
<td>Used internally by the Messaging Engine to enable loop back and request-response scenarios.</td>
</tr>
<tr class="odd">
<td>BTS.SPGroupID</td>
<td>Promoted by the Messaging Engine when the message is sent to a send port from orchestration.</td>
<td>xs:string</td>
<td>Specifies the ID of the send port group.</td>
</tr>
<tr class="even">
<td>BTS.SPID</td>
<td>Promoted by the Messaging Engine when a message is sent to a send port from orchestration.</td>
<td>xs:string</td>
<td>Specifies the ID of the send port.</td>
</tr>
<tr class="odd">
<td>BTS.SPTransportBackupID</td>
<td>Promoted by the Messaging Engine when a message is sent to a send port from an orchestration.</td>
<td>xs:string</td>
<td>Specifies the ID of the backup adapter in the send port.</td>
</tr>
<tr class="even">
<td>BTS.SPTransportID</td>
<td>Promoted by the Messaging Engine when a message is sent to a send port from an orchestration.</td>
<td>xs:string</td>
<td>Specifies the ID of the primary adapter in the send port.</td>
</tr>
<tr class="odd">
<td>BTS.SuspendAsNonResumable</td>
<td>This property can be set by an adapter before calling SubmitMessage() or in an orchestration before sending a message to a send port.<br />
<br />
 <strong>Note</strong> SubmitRequestMessage() will ignore this property; two-way messages are always suspended as non-resumable.</td>
<td>xs:boolean</td>
<td>Controls whether the Message Engine should suspend a message as non-resumable on message failure. Typically messages are suspended as resumable but there are cases when this is inappropriate -- for example, resuming a message for an ordered send or receive port would break message order.<br />
<br />
Valid values:<br />
<br />
- False. Message is suspended as resumable (this is the default).<br />
<br />
- True. Message is suspended as non-resumable.</td>
</tr>
<tr class="even">
<td>BTS.SuspendMessageOnRoutingFailure</td>
<td>Promoted by the Messaging Engine after receiving a message from a receive adapter and before publishing it into the MessageBox database.</td>
<td>xs:boolean</td>
<td>Specifies behavior when a routing failure occurs with an incoming message.<br />
<br />
Valid values:<br />
<br />
- Default / False. If the property does not exist or is set to False, the engine notifies the adapter of the error when a routing failure occurs.<br />
<br />
- True. The routing engine will suspend the message automatically when a routing failure occurs.<br />
<br />
 <strong>Note</strong> The suspended message will be the post-pipeline/mapping message and not the message submitted by the adapter (i.e. the wire message).</td>
</tr>
</tbody>
</table>


There are a number of other properties in this namespace that carry information that may be useful for some BizTalk applications.

<table>
<thead>
<tr class="header">
<th>Property</th>
<th>When and where it is promoted</th>
<th>Type</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>BTS.AckDescription</td>
<td>Set by the Messaging Engine before publishing an acknowledgement message into the MessageBox database.</td>
<td>xs:string</td>
<td>Identifies the <strong>ErrorDescription</strong>, which gives the place and reason for the suspension.</td>
</tr>
<tr class="even">
<td>BTS.EncryptionCert</td>
<td>Not promotable.</td>
<td>xs:int</td>
<td>Identifies the thumbprint corresponding to the encryption certificate. Set this property in an orchestration or custom pipeline component placed before the MIME/SMIME Encoder pipeline component in a pipeline to perform response encryption on a request-response port that is receiving a signed and encrypted message.</td>
</tr>
<tr class="odd">
<td>BTS.InterchangeID</td>
<td>Set by the Messaging Engine for each message that arrives on the server.</td>
<td>xs:string</td>
<td>Defines the unique ID that is used to group the documents that resulted from the same interchange message.</td>
</tr>
<tr class="even">
<td>BTS.Loopback</td>
<td>Set by an adapter when submitting the request message for loop back execution.</td>
<td>xs:boolean</td>
<td>Defines whether the message should be submitted into the server for a loop back execution. In loop back execution, the request message is published into the MessageBox database where it is routed directly to the receive adapter as a response.</td>
</tr>
<tr class="odd">
<td>BTS.SignatureCertificate</td>
<td>Set by some adapters when submitting a message into the server. This property is used by the Party Resolution pipeline component.</td>
<td>xs:string</td>
<td>Identifies the thumbprint of the signing certificate that was used to sign the message received by BizTalk Server.</td>
</tr>
<tr class="even">
<td>BTS.SourcePartyID</td>
<td>Set by the Party Resolution pipeline component after the party has been identified for the incoming message.</td>
<td>xs:string</td>
<td>The ID of the BizTalk party.</td>
</tr>
<tr class="odd">
<td>BTS.SSOTicket</td>
<td>If the receive adapter supports this property, it is set when publishing the message to a server.</td>
<td>xs:string</td>
<td>A ticket contains the encrypted domain and username of the current user, as well as the ticket expiration time. The ticket is used by SSO enabled adapters to get the credentials for the user when authenticating with destination endpoints.</td>
</tr>
<tr class="even">
<td>BTS.WindowsUser</td>
<td>Set by some adapters when submitting a message into the server. This property is used by the Party Resolution pipeline component.</td>
<td>xs:string</td>
<td>Specifies the account of a user on behalf of which the message is submitted into the server.</td>
</tr>
</tbody>
</table>


## See Also

[About BizTalk Message Context Properties](https://msdn.microsoft.com/en-us/library/aa578366\(v=bts.80\))  
[Message Context Properties](message-context-properties1.md)

