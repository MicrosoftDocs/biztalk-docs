---
title: "AS2 Context Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b4d63104-f31e-4ed2-b294-ba3ea8a39ae6
caps.latest.revision: 23
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# AS2 Context Properties
Five types of context properties apply to AS2 messages in BizTalk Server:  

-   Context properties in the EdiIntProperties.xsd schema  

-   Context properties internal to BizTalk Server  

-   Context properties internal to BizTalk MIME  

-   Context properties internal to AS2  

-   Context properties internal to AS2 Status Reporting  

## Context Properties in the EdiIntProperties.xsd schema  
 The message context properties in the EDI/INT global property schema are publicly exposed so you can use them in operations such as message routing. These context properties are defined in EdiIntProperties.xsd in the `Microsoft.BizTalk.Edi.BaseArtifacts` assembly. The namespace for the properties is `http://schemas.microsoft.com/BizTalk/2006/as2-properties`. If they are promoted, these message context properties are available as `EdiIntAS.<Property Name>` in the **Filters** page of the **Send Port Properties** dialog box.  

|Name|Type|Description|  
|----------|----------|-----------------|  
|AS2From|string|Contains the AS2-From AS2 header value that represents the sender’s name.|  
|AS2PayloadContentType|string|Contains the content type of the payload message.|  
|AS2To|string|Contains the AS2-To AS2 header value that represents the receiver’s name.|  
|DispositionMode|string|Contains the MDN disposition mode value.<br /><br /> Both this context property and the DispositionType context property must be promoted in order for an MDN to be generated.|  
|DispositionType|string|Contains the MDN disposition type value.<br /><br /> Both this context property and the DispositionMode context property must be promoted in order for an MDN to be generated.|  
|IsAS2AsynchronousMdn|boolean|Indicates that the message is an asynchronous MDN.|  
|IsAS2FailedMessage|boolean|Indicates that the incoming AS2 message has failed processing in AS2, causing the payload message to be suspended.|  
|IsAS2Http200OKResponse|boolean|Set on a message that will be generated as an HTTP 200 OK response message. It is used when an MDN will not be generated for an AS2 message or when the MDN is being sent asynchronously.|  
|IsAS2MdnResponseMessage|boolean|Indicates that the message is an MDN response message.|  
|IsAS2MessageDuplicate|boolean|Indicates that the incoming AS2 message has previously been received.|  
|IsAS2MessageCompressed|boolean|Indicates that the incoming AS2 message was compressed.|  
|IsAS2MessageEncrypted|boolean|Indicates that the incoming AS2 message was encrypted.|  
|IsAS2MessageSigned|boolean|Indicates that the incoming AS2 message was signed.|  
|IsAS2PayloadMessage|boolean|Indicates that this message contains the decoded AS2 message content and should be processed as the payload.|  
|MDNAsyncURI|string|Contains the **Receipt-Delivery-Option** value that is used in sending asynchronous MDN response messages.|  
|MessageId|string|Contains the AS2 Message ID that is included in the headers of the AS2 message.|  
|OriginalMessageId|string|Contains the Message ID of the original AS2 Message. This context property is part of an MDN message and is used for correlating AS2 Messages and their MDN Responses.|  
|PreservedFileName|string|Contains the original file name of the message. This context property will only be populated if the incoming message includes filename information as part of the Content-Disposition MIME header.|  
|SendMDN|boolean|Set to true if an MDN message should be generated.|  

## Context Properties Internal to BizTalk Server  
 The following message context properties are not publicly exposed, so you cannot use them for operations such as message routing. However, they can be viewed in suspended and tracked messages. The namespace for these context properties is `http://schemas.microsoft.com/BizTalk/2006/system-properties`.  


|                  Name                  |  Type   |                                                                                            Description                                                                                             |
|----------------------------------------|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| IgnoreSslCertificateNameMismatchErrors | boolean |                  Directs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HTTP processing to ignore SSL name mismatch errors during processing.                  |
|               KeepAlive                | Boolean |                                                                    Controls the behavior of the HTTP Keep Alive functionality.                                                                     |
|        TreatEPMSuspendAsSuccess        | boolean | Directs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to treat a suspended message as a success message when processing on a two-way HTTP inbound connection. |
|           IsSolicitResponse            | boolean |                      Set by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and indicates that the message is a solicit-response message.                       |

## Context Properties Internal to BizTalk MIME  
 The following message context properties are not publicly exposed, so you cannot use them for operations such as message routing. However, they can be viewed in suspended and tracked messages. The namespace for these context properties is `http://schemas.microsoft.com/BizTalk/2006/system-properties`.  


|                  Name                   |  Type   |                                                                                     Description                                                                                     |
|-----------------------------------------|---------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            IsMultipartReport            | boolean |                 Causes the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MIME encoder to generate a multipart/report message.                  |
| SuppressMimeVersionFromMultiPartMessage | boolean | Causes the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MIME encoder to suppress the MIME Version header in each part of a multipart message. |

## Context Properties Internal to AS2  
 The following message context properties are not publicly exposed, so you cannot use them for operations such as message routing. However, they can be viewed in suspended and tracked messages. The namespace for these context properties is `http://schemas.microsoft.com/BizTalk/2006/as2-properties`.  

|Name|Type|Description|  
|----------|----------|-----------------|  
|MicHashAlgorithm|string|Contains the hash algorithm used when computing the MIC hash value.|  
|ReceivedContentMic|string|Contains the calculated MIC hash value.|  

## Context Properties Internal to AS2 Status Reporting  
 The following message context properties are not publicly exposed, so you cannot use them for operations such as message routing. However, they can be viewed in suspended and tracked messages. The namespace for these context properties is `http://schemas.microsoft.com/BizTalk/2006/edi-properties`.  

|Name|Type|Description|  
|----------|----------|-----------------|  
|InterchangeControlNo|string|The interchange control number from an EDI interchange. This property is read from a message during AS2 encoding and is used to report an AS2 Interchange Activity.|  
|InterchangeDate|string|The interchange date from an EDI interchange. This property is read from a message during AS2 encoding and is used to report an AS2 Interchange Activity.|  
|InterchangeTime|string|The interchange time from an EDI interchange. This message context property is read from a message during AS2 encoding and is used to report an AS2 Interchange Activity.|  
|ReceiverID|string|The interchange receiver ID from an EDI interchange. This property is read from a message during AS2 encoding and is used to report an AS2 Interchange Activity.|  
|ReceiverQualifier|string|The interchange receiver qualifier from an EDI interchange. This property is read from a message during AS2 encoding and is used to report an AS2 Interchange Activity.|  
|SenderID|string|The interchange sender ID from an EDI interchange. This property is read from a message during AS2 encoding and is used to report an AS2 Interchange Activity.|  
|SenderQualifier|string|The interchange sender qualifier from an EDI interchange. This property is read from a message during AS2 encoding and is used to report an AS2 Interchange Activity.|  

## See Also  
 [Developing and Configuring BizTalk Server AS2 Solutions](../core/developing-and-configuring-biztalk-server-as2-solutions.md)