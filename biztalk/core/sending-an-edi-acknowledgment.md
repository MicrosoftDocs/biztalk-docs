---
title: "Sending an EDI Acknowledgment | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4a036d08-8a65-43ad-b72c-2a246d302792
caps.latest.revision: 31
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Sending an EDI Acknowledgment
Acknowledgments indicate the status of EDI message transmission. After [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives an EDI interchange, it will return one or more acknowledgments to the sender of an EDI interchange, depending upon which acknowledgments have been enabled.  
  
 Based on the level of validation, EDI message acknowledgments fall into two types:  
  
- A **Technical Acknowledgment** generated as a result of header validation. The technical acknowledgment reports the status of the processing of an interchange header and trailer by the address receiver.  
  
- A **Functional Acknowledgment** generated as a result of body validation. The functional acknowledgment reports each error encountered while processing the received document.  
  
  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] can return both technical and functional acknowledgments in response to a single interchange. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] returns a single technical acknowledgment for each interchange. For X12 interchanges, it will return a functional acknowledgment for each group received. For EDIFACT interchanges, it will return a functional acknowledgment for each interchange, no matter how many groups that interchange contains.  
  
## X12 Acknowledgments  
 **X12 Technical Acknowledgment**  
  
 A positive TA1 acknowledgment is sent if the ISA header and the IEA trailer of an X12 message are valid (irrespective of other content). For more information on the contents of a TA1 acknowledgment, see [X12 TA1 Acknowledgment](../core/x12-ta1-acknowledgment.md).  
  
 **X12 Functional Acknowledgment**  
  
 A 997 acknowledgment is used to acknowledge receipt of an interchange or a functional group, to accept or reject one or more functional groups or one or more transactions, and to verify and report compliance with the standard. If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives an interchange with multiple groups, it will return an acknowledgment for each group. If a group contains multiple transaction sets, the acknowledgment for that group will contain multiple AK2 loops, one for each transaction set, depending upon whether AK2 loops are generated for accepted transaction sets. For more information on the contents of a 997 acknowledgment, see [X12 997 Acknowledgment](../core/x12-997-acknowledgment.md).  
  
> [!NOTE]
>  When the EDI receive pipeline builds the Functional Group Header (GS) segment for the X12 functional ACK, the Application Sender Code (GS02) and Application Receiver Code (GS03) are taken from the functional group being acknowledged. However, GS02 on incoming message is mapped to GS03 on the ACK and GS03 on incoming message is mapped to GS02 on the ACK.  
  
## EDIFACT Acknowledgments  
 **EDIFACT Technical Acknowledgment**  
  
 For EDIFACT, a separate technical acknowledgment is not used, but sections of the functional acknowledgment or CONTRL ACK (see below) are reused for the receipt ACK. This emulates a technical acknowledgment.  
  
 For more information on the technical CONTRL acknowledgment, see [EDIFACT CONTRL Message as Technical Acknowledgment](../core/edifact-contrl-message-as-technical-acknowledgment.md).  
  
 **EDIFACT Functional Acknowledgment**  
  
 For EDIFACT, the functional CONTRL acknowledgment is used to acknowledge a received interchange, group, and message; accept or reject a received interchange, group, and message; and to list any syntactical errors or unsupported functionality contained in them. The CONTRL ACK reports the results of a syntactical check of the complete received interchange.  
  
 For more information on the functional CONTRL acknowledgment, see [EDIFACT CONTRL Message as Functional Acknowledgment](../core/edifact-contrl-message-as-functional-acknowledgment.md).  
  
## When an Acknowledgment Is Generated  
 The EDI receive pipeline will generate an acknowledgment if either of the following conditions are met:  
  
- A data element in the received interchange prompts the acknowledgment. For X12-encoded messages, the receive pipeline will generate a technical TA1 ACK if the ISA14 data element is set to 1. For EDIFACT-encoded messages, the receive pipeline will generate a technical CONTRL ACK if the UNB9 data element is set to 2, and it will generate a functional CONTRL ACK if the UNB9 data element is set to 1.  
  
- An agreement property prompts the acknowledgment. For X12 interchanges, these properties are the **TA1 Expected** and **997 Expected** properties in the **Acknowledgements** page of the bi-directional agreement tabs of the **Agreement Properties** dialog box. For EDIFACT interchanges, these properties are the **Receipt of message (CONTRL) expected** and **Acknowledgement (CONTRL) expected** in the **Acknowledgements** page of the bi-directional agreement tabs of the **Agreement Properties** dialog box. When you enable a type of acknowledgment, you can also indicate whether to batch that type of acknowledgment.  
  
- A global property prompts the acknowledgment when no agreement is determined for the interchange. These properties are the  
  
  -   **TA1 Expected** and **997 Expected** properties in the **Acknowledgements** page of the agreement tab of the **X12 Fallback Settings** dialog box.  
  
  -   **Receipt of message (CONTRL) expected** and **Acknowledgement (CONTRL) expected** in the **Acknowledgements** page of the agreement tab of the **EDIFACT Fallback Settings** dialog box.  
  
  For EDIFACT, the EDI receive pipeline will return two separate CONTRL acknowledgments if both a technical acknowledgment and a functional acknowledgment are prompted. The technical CONTRL ACK will include receipt acknowledgment information only. The functional CONTRL ACK will include both receipt information and functional acknowledgment information. For more information, see [EDIFACT CONTRL Acknowledgment](../core/edifact-contrl-acknowledgment.md).  
  
## Identifying an Acknowledgment with a Control Number  
 Each acknowledgment needs to be identified by a transaction set control number for X12 (the ST2 data element) or a transaction set reference number for EDIFACT (the UNH1 data element). If an agreement is configured for the outgoing acknowledgment, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will set the transaction set control or reference number to the value set for the agreement based on the following:  
  
- **For X12 acknowledgements** – (**ACK Control number (ST02)** property in **Local Host Settings** Page (**Receiver’s Settings** section) of the agreement tab in **Agreement Properties** dialog box  
  
- **For EDIFACT acknowledgements** – (**Edifact Ack Control number** property in **Local Host Settings** Page (**Receiver’s Settings** section) of the agreement tab in **Agreement Properties** dialog box  
  
  If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] does not determine the agreement for the acknowledgment, it will use the same properties as mentioned above but available on the agreement tab in the **X12 Fallback Settings** ad **EDIFACT Fallback Settings** dialog boxes. This setting applies to both the technical and functional acknowledgments if both are configured. This integer will be incremented by one for each acknowledgment or interchange generated.  
  
  The envelope of an acknowledgment is built from data in the received message according to the acknowledgment control schema.  
  
## Preparing the Acknowledgment  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] builds the envelope for an acknowledgment just as it builds an envelope for a message, by looking at the definitions of the Interchange Control Header and the Functional Group Header. For more information, see [Agreement Resolution and Schema Determination for Outgoing EDI Messages](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md).  
  
 To enable seamless routing of the generated acknowledgment (TA1, 997, or CONTRL), the EDI Disassembler will populate the `DestinationPartyReceiverQualifier`, `DestinationPartyReceiverIdentifier`, `DestinationPartySenderQualifier`, and `DestinationPartySenderIdentifier` properties on the acknowledgment.  
  
## Synchronous and Asynchronous Acknowledgments  
 You can choose to send EDI acknowledgments either synchronously or asynchronously. If synchronous, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will route the acknowledgment directly to the send pipeline of a two-way request-response receive port. If asynchronous, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will route the acknowledgment to the MessageBox, and a send port will subscribe to that message.  
  
 To specify that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sends the acknowledgment synchronously, select **Route ACK to send pipeline on request-response receive port** in the **Local Host Settings** page (**Receiver’s Settings** section) under **Interchange Settings** in the bi-directional agreement tab (for both X12 and EDIFACT agreements). If you clear this property, the send pipeline of the two-way receive port must be set up to return an EDI interchange.  
  
 If a scenario uses a request-response receive port, and both a technical acknowledgment and a functional acknowledgment are enabled, the technical acknowledgment will be sent back synchronously, and the functional acknowledgment will be sent back asynchronously.  
  
 When receiving an EDIINT/AS2-encoded message over HTTP/HTTPS, if an MDN is sent out in response to a MIME wrapped EDI payload (on the same socket), then an EDI acknowledgment will not be sent out synchronously. If in this case the **Route ACK to send pipeline on request-response receive port** property is checked, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will ignore the property.  
  
## See Also  
 [EDI Acknowledgment Structure](../core/edi-acknowledgment-structure.md)   
 [EDI Service and Control Schemas](../core/edi-service-and-control-schemas.md)   
 [X12 TA1 Acknowledgment](../core/x12-ta1-acknowledgment.md)   
 [X12 997 Acknowledgment](../core/x12-997-acknowledgment.md)   
 [EDIFACT CONTRL Acknowledgment](../core/edifact-contrl-acknowledgment.md)   
 [EDIFACT CONTRL Message as Technical Acknowledgment](../core/edifact-contrl-message-as-technical-acknowledgment.md)   
 [EDIFACT CONTRL Message as Functional Acknowledgment](../core/edifact-contrl-message-as-functional-acknowledgment.md)