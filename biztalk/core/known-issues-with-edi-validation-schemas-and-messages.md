---
title: "Known Issues with EDI Validation, Schemas, and Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 417c3e18-9a97-4d59-bc2b-e96a8c33d388
caps.latest.revision: 42
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Known Issues with EDI Validation, Schemas, and Messages
This topic describes known validation issues.  
  
## Message Is Suspended with EDI Validation Turned Off  
 **Symptom**  
  
 A paired rule is violated, and validation is turned off, but the message is suspended (expected results are that the message is serialized).  
  
 **Possible Cause**  
  
 Cross-field/segment validation is performed, even if **EDI type** property is deselected in the **Validation and ACK Generation Settings** node of the **EDI Properties** dialog box. Validation occurs because it is turned on in the schema annotation.  
  
 **Resolution**  
  
 Turn off validation in the schema annotation.  
  
## The BizTalk service needs to be restarted after a schema has been edited and redeployed  
 **Symptom**  
  
 BizTalk Server does not successfully process a valid message after a schema has been edited and redeployed.  
  
 **Possible Cause**  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] caches schemas with unlimited timeouts.  
  
 **Resolution**  
  
 After editing and redeploying a schema, restart the BizTalk Server Application service. You also must restart the host instance hosting the pipeline that is using the redeployed schema.  
  
## Processing Has Been Aborted for Messages of a Single Encoding Type for a Single Party  
 **Symptom**  
  
 The processing of all messages of a single encoding type (for example, X12 or EDIFACT) for a single party have been aborted. Processing of messages of another encoding type for the same party, or any messages for another party, has not been affected.  
  
 **Possible Cause**  
  
 The length of the interchange, group, or transaction set control number has exceeded the maximum allowable length.  
  
 For X12 messages, the maximum length of a control number is nine digits. For EDIFACT message, the maximum length of a control number is 14 digits over three fields.  
  
 **Resolution**  
  
 Reset the control number in the appropriate property page of the EDI Properties dialog box for the affected party. You can edit the control numbers in the following property pages:  
  
-   X12 interchange control number: ISA Segment Definition page (in the Party as Interchange Receiver node) for X12 Properties  
  
-   X12 group or transaction set control number: GS and ST Segment Definition page (in the Party as Interchange Receiver node for X12 Properties)  
  
-   EDIFACT interchange control number: UNB Segment Definition page (in the Party as Interchange Receiver node for EDIFACT Properties)  
  
-   EDIFACT group or transaction set control number: UNG and UNH Segment Definition page (in the Party as Interchange Receiver node for EDIFACT Properties)  
  
## BizTalk Server validates with schemas that have UNH segments with seven data elements  
 In earlier versions of EDIFACT, the UNH segment has four elements, rather than the seven elements (three of which are optional) that the UNH segment has in later versions. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses the later version with seven elements for validation.  
  
## Error messages generated for multiple cross-field validation rules will not be specific to the rule  
 If a schema contains multiple cross-field validation rules for a data element in a message, and an error occurs with the data element, a separate error will be generated for each validation rule. However, each of these errors will have the same error code and description; the errors will not be specific to the validation rule.  
  
## If EDI type validation is disabled on receive and enabled on send, the send pipeline will not be able to serialize the message  
 If you turn off EDI type validation on the receive side, the EDI receive pipeline will generate an XML message from a received EDI message, whether or not the message is valid. If EDI validation is enabled on the send side, the EDI send pipeline will not be able to reprocess the XML into a valid EDI file if the XML file contains errors, and as a result will generate an error.  
  
## EDI promoted properties are only available if your application has a reference to the BizTalk EDI application  
 **Symptom**  
  
 Promoted properties under the EDI namespace are not displayed in the list of promoted properties that you are trying to use, for example, in an orchestration or in the filter conditions for a send port.  
  
 **Possible Cause**  
  
 The BizTalk application that you are using does not have a reference to the BizTalk EDI Application. The property schemas for the EDI promoted properties are in Microsoft.BizTalk.Edi.BaseArtifacts.dll, which is included in the Resources folder of BizTalk EDI Application.  
  
 **Resolution**  
  
 To the BizTalk application that you are working in, add a reference to the BizTalk EDI Application.  
  
## The Data Element Name in a Context Property Name Contains an Underscore, Not a Period  
 The name of a data element within an EDI segment contains a period, for example, UNB2.1, which is the identification field for the UNB2 Sender segment. However, when the data element name is included as part of an EDI context property, the period is replaced with an underscore. For example, the context property for the Sender Identification data element is EDI.UNB2_1, not EDI.UNB2.1. The reason for this is that a period is not supported in a context property name.  
  
## Irrelevant string is appended to instance validation error message  
 Whenever you receive an error during instance validation, the string "BEC 2004" will be appended to the error message. You can ignore this string.  
  
## EDIFACT Schema Names Are Case-Sensitive  
 The schema name of an EDIFACT schema, as shown in the root_reference data element of the schema, is case-sensitive. For example, EFACT_D98B_ORDERS and EFACT_d98B_Orders would be two different schemas.  
  
## Invalid EDI Messages Can Be Suspended Even If EDI Type Validation Is Disabled  
 EDI structural validation is performed even if the EDI Type validation is disabled. An interchange that fails the basic structural validations will be suspended, even if the EDI Type validation is disabled.  
  
## The EDI Assembler Will Serialize an Unbatched Interchange Even If a Separator Character Is Used in an Envelope Header  
 The separator characters used to separate header and trailer fields must not be used in the definition of any of the interchange, group, or transaction set header or trailer fields, as defined for the party as interchange receiver. If they are, the interchange will fail processing either in the EDI Assembler of the sending BizTalk Server or in the disassembler of the receiving party. The interchange will fail in the EDI Assembler if it is an outbound batch, because the Assembler will validate the envelope against the header control (service) schema. If the interchange is unbatched, the EDI Assembler will serialize it, but it will fail processing in the disassembler at the receiving party.  
  
## Mismatched Character Sets Can Result in Suspended Interchanges  
 The character set used for an outgoing interchange should be the same as the character set used to create the transaction sets inserted into the interchange. If not, the interchange will likely be suspended with an error message indicating that there were invalid characters.  
  
 For example, if you create an EDIFACT batch using the UNOA character set, but a transaction set added to the batch has lower-case characters, the batching orchestration will suspend the message because UNOA does not allow lower-case characters.  
  
 As another example, if you configure the EDI send pipeline for X12 interchanges with the "Basic" character set, but an X12 batched interchange has lower-case characters because the X12 character set selected in the X12 Interchange Envelop Generation page for the party as an interchange receiver is set to "Extended" or "UTF8/Unicode", the batched message will be suspended when envelope settings are applied.  
  
## Using UNH2.5 for schema resolution requires an update to the schema  
 If you use UNH2.5 (the Association assigned code) for schema resolution of an incoming EDIFACT interchange, you will need to update the relevant document schema in the \Program Files\Microsoft BizTalk Server 20xx\Schema folder. You will need to append the value of UNH2.5 to the existing values for the root_reference, display_reference, and xs:element name. For example, if UNH2.5 is "EAN008" and you are using the EFACT_D96A_INVOIC schema, you would set root_reference, display_reference, and xs:element name to "EFACT_D96A_INVOIC_EAN008".  
  
## The compressed file of schemas will be replaced when an upgrade is performed  
 If you upgrade Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to a later build, the MicrosoftEdiXSDTemplates.exe file in your installation will be replaced with the MicrosoftEdiXSDTemplates.exe file associated with the upgrade. If you plan to continue to use the schemas from the old compressed file, you will no longer have access to the compressed file after the upgrade unless you back up the old compressed file.  
  
## If a group contains multiple X12 transaction sets, all must be of the same type  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] does not support mixing different transaction sets within the same group. When a group contains multiple transactions, the value of ST01 must be the same for all transactions.  
  
## Receiving X12 interchanges that contain non-ASCII delimiters may result in the message becoming suspended  
 **Symptom**  
  
 When receiving an X12 interchange that uses non-ASCII delimiter values, the message may become suspended and an error written to the application event log.  
  
 **Possible Cause**  
  
 This problem can occur if the interchange is not encoded as UTF-8.  
  
 **Resolution**  
  
 Ensure that any incoming X12 interchange that contains non-ASCII delimiters is encoded as UTF-8.  
  
## See Also  
 [Known Issues with EDI Processing](../core/known-issues-with-edi-processing.md)   
 [EDI Messaging](../core/edi-messaging.md)   
 [EDI Message Validation](../core/edi-message-validation.md)   
 [EDI Schemas](../core/edi-schemas.md)   
 [Developing EDI Schemas](../core/developing-edi-schemas.md)