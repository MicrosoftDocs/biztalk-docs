---
title: "How the EDI Disassembler Works | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8da91ba4-e1c9-4e6b-bbd1-fe71ea880118
caps.latest.revision: 43
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How the EDI Disassembler Works
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] performs most processing for received EDI-encoded interchanges in the EDI Receive Pipeline (`Microsoft.BizTalk.DefaultPipelines.EDIReceivePipeline`). This pipeline includes the EDI disassembler pipeline component, which performs the following processing:  
  
- Splits multiple interchanges in a single message into separate interchanges (if the "DetectMID" pipeline property for the receive location is set to True). The EDI Disassembler does so by searching for an interchange control header (ISA, UNA, or UNB) even after an interchange control trailer (IEA or UNZ) has been encountered.  
  
- Validates the envelope.  
  
- Disassembles the interchange.  
  
- Processes trigger fields for HIPAA interchanges.  
  
- Validates EDI and partner-specific properties, as applicable. This includes EDI schema validation, cross-field validation for X12-encoded messages (if configured), EDI structural validation, and extended schema validation (if the schema was customized with a node that has a non-EDI data type). For more information, see [Validation of Received EDI Messages](../core/validation-of-received-edi-messages.md).  
  
- Verifies that the interchange, group, and transaction set control numbers are not duplicates, if the checks are enabled in the **Validation** page (under **Interchange Settings**) of the bi-directional agreement tab of the **Agreement Properties** dialog box. Check the interchange control number against previously received interchanges. Checks the group control number against other group control numbers in the interchange. Checks the transaction set control number against other transaction set control numbers in that group. If a duplicate is discovered, the status report will indicate that a duplicate record exists.  
  
- Generates an XML document for each transaction set. On each XML file, promotes the context property of BTS.MessageType, setting it to the schema name with namespace.  
  
- Converts the entire interchange to XML if the **Inbound batch processing option** property is set to one of the two **Preserve Interchange** values. This property can is set from the **Local Host Settings** page under **Interchange Settings** of the bi-directional agreement tab of the **Agreement Properties** dialog box. The receive pipeline promotes the property ReuseEnvelope to identify the interchange as preserved.  
  
- Generates a Technical and/or Functional acknowledgment (if configured). This can include batching the acknowledgments (if configured). Promotes the context property of BTS.MessageType, setting it equal to the control schema in the http://schemas.microsoft.com/EDI/\<X12 or EDIFACT\> namespace (for example, X12_997_Root for a 997 acknowledgment). Also promotes the EDI.DestinationPartyName context property, which ensures that the acknowledgment will be picked up for sending. For more information, see [Sending an EDI Acknowledgment](../core/sending-an-edi-acknowledgment.md).  
  
- Performs HIPAA 276/277 (version 5010 only) 834, 835 (version 4010 only) and 837 document splitting, if applicable.  
  
- Promotes or writes properties to the message context (see next section).  
  
## Promoting or Writing Properties to the Context  
 When the EDI Disassembler processes a received message, it promotes or writes the following properties to the message context:  
  
- For an X12-encoded unbatched message, promotes the following properties from the envelope: ISA06, ISA08, ISA15; GS01, GS02, GS03, GS08; ST03 and ST01.  
  
  > [!NOTE]
  >  For an incoming HIPAA 837 interchange, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] supports three HIPAA 837 schemas: Claim-Dental_837D, Claim-Institutional_837I, and Claim-Professional_837P. The ST01 for each of these is “837".These three schemas have different values for GS08 in version 5010: "005010X223A1" for 837I, "005010X224A1" for 837D, and "005010X222" for 837P. The schemas have different values for GS08 in version 4010: "004010X096A1" for 837I, "004010X097A1" for 837D, and "004010X098A1" for 837P.  
  
- For an EDIFACT-encoded unbatched message, promotes the following properties from the envelope: UNB2.1, UNB2.3, UNB3.1, UNB11; UNG1, UNG2.1, UNG3.1; UNH2.1, UNH2.2, UNH2.3.  
  
- If a batched interchange is split, writes ISA_Segment and GS_Segment to the context for X12-encoded messages, or writes UNA_Segment, UNB_Segment, and UNG_Segment to the context for EDIFACT-encoded messages.  
  
  > [!NOTE]
  >  The above segments are written to the context. They are not promoted to the context. You can, however, append these segments to a transaction set using the Message Enrichment sample. You can also take the code that appends the samples and add it to a custom pipeline component. For more information, see [Message Enrichment Sample (BizTalk Server Sample)](../core/message-enrichment-sample-biztalk-server-sample.md).  
  
  > [!NOTE]
  >  The ISA_Segment promoted property contains security/authorization information (ISA02, Authorization Information, and ISA04, Security Information) that may lead to information disclosure. You can use the **Mask security/authorization/password information property in context property** (in **Local Host Settings** page for **Interchange Settings** for bi-directional agreement properties) to replace the each character in the ISA02 and ISA04 fields with a ‘#’ character. This is a one-way process: the ‘#’ characters cannot be converted to actual characters.  
  
- For X12- and EDIFACT-encoded messages, promotes ReuseEnvelope, which indicates whether a batched interchange is split or preserved.  
  
- If a batched interchange is preserved, promotes the following properties:  
  
  -   InboundTransportatLocation  
  
  -   InboundTransportType  
  
  -   ISA05  
  
  -   ISA07  
  
  -   ISA06  
  
  -   ISA08  
  
  -   ISA15  
  
  -   LastInterchangeMessage = {True&#124;False}  
  
  -   MessageType  
  
  -   ReceivePortID  
  
  -   ReceivePortName  
  
  -   ReuseEnvelope  
  
## Parsing the Envelope  
 The EDI receive pipeline uses the header control schema to parse the envelope of a received EDI message and the EDI document schema to parse the transaction sets/messages in the interchange.  
  
 If an EDIINT/AS2-encoded message was received via HTTP/HTTPS transport, the EDI disassembler will inspect the context property BTS.MessageDestination. If that property is set to SuspendQueue, indicating that an error occurred in AS2 processing and the message is to be suspended, the EDI disassembler will act as a passthrough pipeline component, and will suspend the message to the MessageBox.  
  
 During parsing of EDIFACT interchanges, the EDI receive pipeline removes the release indicator used to escape characters. The release indicator is not included in EDI validation. The EDI receive pipeline does not include the release indicator when it computes length restrictions.  
  
 **Character Set**  
  
 For X12 interchanges, the Pipeline Component Properties determine the character set that the EDI Disassembler will use when processing the interchange. It can Basic, Extended, or UTF8/Unicode. The default value is UTF8 For EDIFACT interchanges, the UNB1.1 field determines the character set.  
  
 **Dynamic Separator Discovery**  
  
 When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives an EDI interchange, no agreement properties indicate what the separators in the interchange should be. Instead, the EDI Disassembler discovers what the delimiters are (for either X12 or EDIFACT) at runtime.  
  
 For X12 messages, the EDI Disassembler uses the following characters from within the interchange:  
  
|Separator|Character|  
|---------------|---------------|  
|Data Element Separator|4th character of ISA|  
|Component Element Separator|ISA16|  
|Segment Separator|106th character of ISA|  
|Segment Terminator Suffix|Character between ISA segment and GS segment<br /><br /> **Values:** None, CR, LF, or CRLF **Note:**  The separator can take only the above values.|  
|Repetition Separator or Standard Identifier<br /><br /> (depending on the "ISA11 usage" agreement property on the **Envelopes** page of the bi-directional agreement tab)|ISA11|  
  
 For EDIFACT interchanges, the EDI Disassembler checks the UNA segment that defines the separators in the interchange. If the interchange does not have a UNA segment, which is optional, the Disassembler will use the default values defined in the pipeline component properties.  
  
|Separator|Character of UNA|  
|---------------|----------------------|  
|Component Element Separator|4th|  
|Data Element Separator|5th|  
|Decimal Notation|6th|  
|Release Character|7th|  
|Repetition Character|8th|  
|Segment Separator|9th|  
|Segment Separator Suffix|Character between UNA segment and UNB segment<br /><br /> **Values:** None, CR, LF, or CRLF **Note:**  The separator can take only the above values.|  
  
 The UNA string is optional. If it is present, it defined all the delimiters for the file. If it is not present, the EDI Disassembler will use the EfactDelimiters pipeline component property to determine the delimiters. For more information, see [Configuring EDI Pipeline Properties](../core/configuring-edi-pipeline-properties.md).  
  
 **Posting Errors**  
  
 If the EDI disassembler encounters an EDI processing error, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] posts the following two errors in the Event Viewer (if such posting is enabled):  
  
- An error logged by the source [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] while it suspends the message. This is a required error relating to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processing.  
  
- An error reporting problems in the transaction set, as logged by the source [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI. This error is EDI-specific.  
  
## Using Agreement Properties  
 The EDI Disassembler will use agreement properties if it can identify the agreement (see [Agreement Resolution, Schema Discovery, and Authorization for Received EDI Messages](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md)). If a matching agreement cannot be found and the corresponding values are not available in the fallback agreement as well, the EDI Disassembler properties set in the **Properties** window of Visual Studio will be used. However, this fallback will not occur if authentication is required in receive port properties (if either **Drop messages if authentication fails** or **Keep messages if authentication fails** are selected). In this case, an agreement must be configured; if not, the interchange will be suspended.  
  
 When the EDI Disassembler uses agreement properties, it requires that the following agreement properties be set:  
  
|Property|Agreement Properties Page|  
|--------------|-------------------------------|  
|Repetition separator|**Envelopes** page (under **Interchange Settings**) in the bi-directional agreement tab|  
|Perform EDI Data Type Validation|**Validation** page under **Transaction Set Settings** in the bi-directional agreement tab (for both X12 and EDIFACT agreements)|  
|Extended Validation|**Validation** page under **Transaction Set Settings** in the bi-directional agreement tab (for both X12 and EDIFACT agreements)|  
|Allow leading and trailing zeroes and spaces|**Validation** page under **Transaction Set Settings** in the bi-directional agreement tab (for both X12 and EDIFACT agreements)|  
|Create empty XML Tags if trailing separators allowed|**Local Host Settings** page under **Transaction Set Settings** in the bi-directional agreement tab (for both X12 and EDIFACT agreements)|  
|Inbound batch processing option|**Local Host Settings** page (under **Interchange Settings**) in the bi-directional agreement tab (for both X12 and EDIFACT agreements)|  
|Default EDIFACT Separators|-|  
|Mask security/authorization/password information|**Local Host Settings** page (under **Interchange Settings**) in the bi-directional agreement tab (for both X12 and EDIFACT agreements)|  
|Convert implied decimal format Nn to base 10 numeric value|**Local Host Settings** page under **Transaction Set Settings** in the bi-directional agreement tab (for X12 agreements)|  
|Route ACK to send pipeline on request-response receive port|**Local Host Settings** page (**Receiver’s Settings** section) under **Interchange Settings** in the bi-directional agreement tab (for both X12 and EDIFACT agreements)|  
|X12 character set|X12 Interchange Envelope Generation **Note:**  This setting is only used to validate the values entered for the agreement properties. The X12 character set used for runtime processing is selected in the pipeline properties. For more information, see [EDI Character Sets](../core/edi-character-sets.md).|  
  
## Using HIPAA Trigger Fields  
 EDI segments often contain qualifier values that modify the meaning of the segment. For example, an N1 segment can contain a qualifying element of “BT” to signify a “bill-to name,” or it may contain a qualifying element of “ST” to indicate a “ship-to name.” Normally it is left to business logic to determine how to interpret these fields and the disassembler resolves all instances of the N1 segment to the same XML record name; however, the HIPAA schemas shipped with BizTalk Server contain annotations that allow the EDI disassembler to create unique XML records based on the presence of a qualifying value (see [HIPAA Schema Trigger Field Annotations](../core/hipaa-schema-trigger-field-annotations.md)).  
  
 When receiving a HIPAA transaction set, if the EDI Disassembler encounters a segment that contains a trigger field, it uses the trigger information to generate an XML record specific to the segment and trigger combination.  
  
 The following table shows how an N1 segment will be translated into an XML record based on the value of N101:  
  
|N1 Segment|Resulting XML Data|  
|----------------|------------------------|  
|N1*PR\*Contoso\*XV\*0000000~|`<ns0:TS835W1_1000A_Loop>  <N1_PayerIdentification_TS835W1_1000A>   <N101__EntityIdentifierCode>PR</N101__EntityIdentifierCode>    <N102__PayerName>Contoso</N102__PayerName>    <N103__IdentificationCodeQualifier>XV</N103__IdentificationCodeQualifier>    <N104__PayerIdentifier>0000000</N104__PayerIdentifier>   </N1_PayerIdentification_TS835W1_1000A>`|  
|N1*PE\*Fabrikam\*FI\*9999999~|`<TS835W1_1000B_Loop>   <N1_PayeeIdentification_TS835W1_1000B>    <N101__EntityIdentifierCode>PE</N101__EntityIdentifierCode>    <N102__PayeeName>Fabrikam</N102__PayeeName>    <N103__IdentificationCodeQualifier>FI</N103__IdentificationCodeQualifier>    <N104__PayeeIdentificationCode>9999999</N104__PayeeIdentificationCode>   </N1_PayeeIdentification_TS835W1_1000B>`|  
  
## See Also  
 [How BizTalk Server Receives EDI Messages](../core/how-biztalk-server-receives-edi-messages.md)