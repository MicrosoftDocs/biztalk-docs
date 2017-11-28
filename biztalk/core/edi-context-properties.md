---
title: "EDI Context Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d6a408af-daf5-4e9e-afb3-9fd1795e8c16
caps.latest.revision: 30
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# EDI Context Properties
The message context properties in the EDI global property schema are publicly exposed so you can use them in operations such as message routing. These context properties are defined in PropertySchema.xsd in the Microsoft.BizTalk.Edi.BaseArtifacts assembly. The namespace for the properties is `http://schemas.microsoft.com/ Edi/PropertySchema`. If they are promoted, these message context properties are available as Edi.\<*Property Name*\> in the **Filters** page of the **Send Port Properties Dialog Box** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].


## Context properties list  
 The EDI context properties are also available in an orchestration, as long as a reference to the Microsoft.BizTalk.Edi.BaseArtifacts assembly has been added to the orchestration project.
  
|Name|Type|Description|  
|----------|----------|-----------------|  
|AK901|string|Indicates whether the functional group identified in the AK1 segment of the acknowledgment was accepted or rejected (X12 997 ACK only).|  
|AttachmentId|String|The ID of the message attachment.|  
|AgreementID|Int|Written by EDI receive pipeline. Specifies the ID of the agreement to which the inbound message is resolved. For a fallback agreement this value is 0.|  
|AgreementName|String|Written by EDI receive pipeline. Specifies the name of the agreement to which the inbound message is resolved. For a fallback agreement this value is **BTSGuestParty**.|  
|AgreementNameForSend|String|Used by the EDI send pipeline for agreement resolution for outbound document.|  
|AgreementPartIDForSend|Int|Used by the EDI send pipeline for agreement resolution for outbound document. This value is written by the Batching Orchestration.|  
|AgreementPartIDOnReceive|Int|Written by EDI receive pipeline. Specifies the one-way agreement ID of the agreement to which the inbound message is resolved. For a fallback agreement this value is 0.|  
|BatchElementValidationFailure|boolean|An indication that an error was promoted by the batching system when a batch element failed validation.|  
|BatchEncodingType|string|The type of encoding that BizTalk Server must use to encode an outgoing batched interchange.|  
|BatchId|Int|The batch ID of the batch configuration to use when processing this document, if the document only matches one batch filter.|  
|BatchIds|String|A list of the batch IDs of the matching batch filter sets, if the document matches more than one batch filter.|  
|BatchingError|string|A description of the error promoted by the batching system when it suspended a batch element.|  
|BatchName|String|The name of the batch configuration to use when processing this document.|  
|CodePage|string|The code page to be used to validate the interchange.|  
|CONTRL_UCI4|string|The Action Code field of a CONTRL acknowledgment, indicating whether the interchange was accepted (a value of "8") or rejected because of an error in the UNA or UNB segment (a value of "4") (EDIFACT CONTRL ACK only).|  
|DestinationPartyID (deprecated in [!INCLUDE[prague](../includes/prague-md.md)])|int|The ID of the destination party that the message should be sent to.|  
|DestinationPartyName (deprecated in [!INCLUDE[prague](../includes/prague-md.md)])|string|The name of the destination party that the message should be sent to.|  
|DestinationPartyReceiver<br />Identifier|string|The identifier of the destination party that the message should be sent to. This property can be promoted in a custom component to enable party resolution in the send pipeline.|  
|DestinationPartyReceiver<br />Qualifier|string|The qualifier of the destination party that the message should be sent to. This property can be promoted in a custom component to enable party resolution in the send pipeline.|  
|DestinationPartySender<br />Identifier|string|The identifier of the party sending the message to the destination party. This property can be promoted in a custom component to enable party resolution in the send pipeline.|  
|DestinationPartySender<br />Qualifier|string|The qualifier of the party sending the message to the destination party. This property can be promoted in a custom component to enable party resolution in the send pipeline.|  
|EncodingType|short|The type of encoding that BizTalk Server must use to encode an outgoing message.|  
|ErrorDescription|string|For a suspended message, contains a copy of the error message (similar to the message in the EventViewer).|  
|GS_Segment|string|The complete GS (functional group) segment (X12).<br /><br /> The EDI receive pipeline writes this property to the context when the interchange is split as transaction sets, not when the interchange is preserved.|  
|GS01|string|The Functional Identifier Code (X12)<br /><br /> The EDI receive pipeline promotes this property to the context (if the interchange is not a batched interchange being preserved).|  
|GS02|string|The Application Sender Code (X12)<br /><br /> The EDI receive pipeline promotes this property to the context (if the interchange is not a batched interchange being preserved).|  
|GS03|string|The Application Receiver Code (X12)<br /><br /> The EDI receive pipeline promotes this property to the context (if the interchange is not a batched interchange being preserved).|  
|GS07|string|The Responsible Agency (X12)<br /><br /> The EDI receive pipeline promotes this property to the context (if the interchange is not a batched interchange being preserved).|  
|GS08|string|The Version/Release/Industry Identifier Code (X12)<br /><br /> The EDI receive pipeline promotes this property to the context (if the interchange is not a batched interchange being preserved).|  
|ISA_Segment|string|The complete ISA (interchange control header) segment (X12).<br /><br /> BizTalk Server writes this property to the context when the interchange is split as transaction sets, not when the interchange is preserved.<br /><br /> This property contains security/authorization information (ISA2, Authorization Information, and ISA4, Security Information) that may lead to information disclosure. You can use the Mask security/authorization/password information property (in the **Validation and ACK Generation** page) to replace each character in the ISA2 and ISA4 fields with a “#” character. This is a one-way process: the “#” characters cannot be converted to actual characters.<br /><br /> The EDI receive pipeline writes this property to the context when the interchange is split as transaction sets, not when the interchange is preserved.|  
|ISA05|string|The Interchange Sender Qualifier (X12)<br /><br /> The EDI receive pipeline promotes this property to the context (if the interchange is not a batched interchange being preserved).|  
|ISA06|string|The Interchange Sender ID (X12)<br /><br /> The EDI receive pipeline promotes this property to the context (if the interchange is not a batched interchange being preserved).|  
|ISA07|string|The Interchange Receiver Qualifier (X12)<br /><br /> The EDI receive pipeline promotes this property to the context (if the interchange is not a batched interchange being preserved).|  
|ISA08|string|The Interchange Receiver ID (X12)<br /><br /> The EDI receive pipeline promotes this property to the context (if the interchange is not a batched interchange being preserved).|  
|ISA15|string|The Usage Indicator (X12)<br /><br /> The EDI receive pipeline promotes this property to the context (if the interchange is not a batched being preserved).|  
|IsResendControlMessage|int|Used by the AS2 engine to indicate that an AS2 message send should be retransmitted, as an MDN response has not been received within the configured time.|  
|IsSystemGeneratedACK|boolean|Indicates that the message is an acknowledgment (X12 TA1 or 997, or EDIFACT CONTRL) that was generated by the system. Can be set to True or False.<br /><br /> This is a message context property that is available as EDI.IsSystemGeneratedACK in the **Filters** page of the **Send Port Properties** dialog box.|  
|ReceiverPartyName|String|Written by EDI receive pipeline. Specifies the name of the destination partner provided in the agreement to which the message is resolved. For a fallback agreement this value is **RECEIVE-PARTNER**.|  
|ReceiverPartyNameForSend|String|Used by the EDI send pipeline for agreement resolution for outbound documents.|  
|ReuseEnvelope|boolean|Indicates whether an interchange is preserved or split. If the interchange is preserved, BizTalk Server will reuse the envelope when processing the interchange for sending.|  
|SenderPartyName|String|Written by EDI receive pipeline. Specifies the name of the source partner provided in the agreement to which the inbound message is resolved. For a fallback agreement this value would be **BTS-SENDER**.|  
|SenderPartyNameForSend|String|Used by the EDI send pipeline for agreement resolution for outbound documents.|  
|ST01|string|The Transaction Set Identifier Code (X12)<br /><br /> The EDI receive pipeline promotes this property to the context (if the interchange is not a batched interchange being preserved).|  
|ST03|string|The Version/Release/Industry Identifier Code (X12)<br /><br /> You can write and promote this property to the context and use it for message routing.|  
|TA1_TA104|string|The Engine Behavior field of a TA104 acknowledgment, indicating whether the interchange was accepted (a value of "A"), accepted with errors (a value of "E"), or rejected/suspended (a value of "R") (X12 TA1 ACK only).|  
|ToBeBatched|boolean|Indicates whether the message should be batched with other messages by the batching orchestration.<br /><br /> After batching an interchange, the batching orchestration sets this property to "False".|  
|ToBeRouted|boolean|Indicates that the message should be picked up by the routing orchestration, which creates as many copies of the batch element as there are subscriptions to that element, and then routes the copies to the MessageBox.|  
|UNA_Segment|string|The complete UNA (Service String Advice) segment (EDIFACT)<br /><br /> The EDI receive pipeline writes this property to the context when the interchange is split as transaction sets, not when the interchange is preserved.|  
|UNB_Segment|string|The complete UNB (interchange control header) segment (EDIFACT)<br /><br /> The EDI receive pipeline writes this property to the context when the interchange is split as transaction sets, not when the interchange is preserved.<br /><br /> This property contains security/authorization information (UNB6.1 and UNB6.2) that may lead to information disclosure. You can use the Mask security/authorization/password information property to replace the value in the UNB6.1 and UNB6.2 fields with a “#” character. Note that the “#” character cannot be converted to actual characters.|  
|UNB11|string|The Usage indicator (EDIFACT)<br /><br /> The EDI receive pipeline promotes this property to the context (if the interchange is not a batched interchange being preserved).|  
|UNB2_1|string|The Interchange Sender ID (EDIFACT)<br /><br /> The EDI receive pipeline promotes this property to the context (if the interchange is not a batched interchange being preserved).|  
|UNB2_2|string|The Interchange Sender Code Qualifier (EDIFACT)<br /><br /> The EDI receive pipeline promotes this property to the context (if the interchange is not a batched interchange being preserved).|  
|UNB2_3|string|The Address for Reverse Routing (EDIFACT)<br /><br /> The EDI receive pipeline promotes this property to the context (if the interchange is not a batched interchange being preserved).|  
|UNB3_1|string|The Interchange Recipient ID (EDIFACT)<br /><br /> The EDI receive pipeline promotes this property to the context (if the interchange is not a batched interchange being preserved).|  
|UNB3_2|string|The Interchange Recipient Code Qualifier (EDIFACT)<br /><br /> The EDI receive pipeline promotes this property to the context (if the interchange is not a batched interchange being preserved).|  
|UNG_Segment|string|The complete UNG (functional group) segment (X12)<br /><br /> The EDI receive pipeline writes this property to the context when the interchange is split as transaction sets, not when the interchange is preserved.|  
|UNG1|string|The Functional Group Identification (EDIFACT)<br /><br /> The EDI receive pipeline promotes this property to the context (if the interchange is not a batched interchange being preserved).|  
|UNG2_1|string|The Application Sender’s Identification (EDIFACT)<br /><br /> The EDI receive pipeline promotes this property to the context (if the interchange is not a batched interchange being preserved).|  
|UNG3_1|string|The Application Recipient’s Identification (EDIFACT)<br /><br /> The EDI receive pipeline promotes this property to the context (if the interchange is not a batched interchange being preserved).|  
|UNH2_1|string|The Message Type (EDIFACT)<br /><br /> The EDI receive pipeline promotes this property to the context (if the interchange is not a batched interchange being preserved).|  
|UNH2_2|string|The Message Version Number (EDIFACT)<br /><br /> The EDI receive pipeline promotes this property to the context (if the interchange is not a batched interchange being preserved).|  
|UNH2_3|string|The Message Release Number (EDIFACT)<br /><br /> The EDI receive pipeline promotes this property to the context (if the interchange is not a batched interchange being preserved).|  
  
## Extracting Individual Fields from the Segment Context Properties  
 Some properties are not written or promoted to the message context by the EDI receive pipelines as individual properties, but only as part of a segment string. This is done for performance reasons, because property promotion has an impact on performance. For example, the ISA5, ISA6, ISA7, ISA8, and ISA15 fields of the ISA segment are promoted by the receive pipelines as individual properties, but the rest of the ISA fields are only written to the message context as part of the ISA_Segment property. These properties are written or promoted only when **ReuseEnvelope** is not set to True, indicating that a received batched interchange is not being preserved.  
  
 If you need an individual field of one of the segments (ISA, GS, UNB, UNG, or UNA) to be written to the message context, but this individual field is not written to the message context by default, you will need to write a custom component to write it to the message context. This custom component needs to parse the segment fields and write an individual field to the message context.  
  
 The Message Enrichment sample shows how to use a parser to extract individual fields from the segments and write them to the context. This sample is included in the \<drive\>:\Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]\SDK\Samples\EDI\MessageEnrichment. For more information, see [Message Enrichment Sample (BizTalk Server Sample)](../core/message-enrichment-sample-biztalk-server-sample.md).  
  
## See Also  
 [Developing and Configuring BizTalk Server EDI Solutions](../core/developing-and-configuring-biztalk-server-edi-solutions.md)