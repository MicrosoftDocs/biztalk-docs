---
title: "How the EDI Assembler Works | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c3785870-08ab-4fc2-8f7e-7c5a37639a7a
caps.latest.revision: 33
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How the EDI Assembler Works
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] performs most processing of EDI-encoded interchanges to be sent in the EDI Send Pipeline (`Microsoft.BizTalk.DefaultPipelines.EDISendPipeline`). This pipeline includes the EDI assembler pipeline component, which performs the following processing:  
  
-   Serializes the EDI interchange, converting XML-encoded messages into EDI transaction sets in the interchange.  
  
-   Performs EDI schema validation, cross-field validation for X12-encoded messages (if configured), EDI structural validation, and extended schema validation (if the schema was customized with a node that has a non-EDI data type).  
  
-   Applies an envelope to the EDI message.  
  
-   Processes Technical and Functional acknowledgments received in response to EDI messages, debatching the acknowledgments if configured.  
  
## Applying an Envelope to an Outgoing EDI Message  
 When the EDI send pipeline builds an outgoing EDI message from an intermediate XML file, it applies an envelope containing interchange and group headers to the message based upon the EDI properties established for the receive-side agreement. If the send pipeline was not able to determine the receiving agreement from the send port, it will use the fallback agreement to apply the envelope.  
  
 If the `EdiOverride.OverrideEdiHeader` context property is set to true, the EDI send pipeline will use values specified in the EdiOverride property collection to construct the envelope. If a value is not present in the collection, the corresponding EDI value in agreement properties will be used. If a value does not exist in either the EdiOverride collection or the agreement properties, the properties in the fallback EDI agreement will be used.  
  
 If the intermediate XML file has a reserved tag or the ReuseEnvelope context property, the message is a preserved batch and the envelope application logic will not apply.  
  
### Sources for X12 Envelope Values  
 The following table shows where the EDI send pipeline gets the information it needs for each part of an X12 envelope:  
  
|Header|Source|  
|------------|------------|  
|Interchange Control Header (ISA)|-   EdiOverride context properties (if `EdiOverride.OverrideEdiHeader` is true).<br />-   If an agreement is defined, ISA segment definitions from different pages under the **Interchange Settings** section in the one-way agreement properties in the **Agreement Properties** dialog box.<br />-   If no agreement is defined, ISA segment definitions from different pages under the **Interchange Settings** section in the **EDIFACT Fallback Settings** dialog box.|  
|Functional Group Headers (GS)|-   EdiOverride context properties (if `EdiOverride.OverrideEdiHeader` is true)<br />-   If an agreement is defined, GS segment definitions from the **Envelopes** page (under **Transaction Set Settings** section) in the one-way agreement properties in the **Agreement Properties** dialog box<br />-   If no agreement is defined, GS segment definitions from the **Envelopes** page (under **Transaction Set Settings** section) in the **X12 Fallback Settings** dialog box<br /><br /> If an agreement is defined, the values for the GS data elements are determined based upon the combination of the Transaction Set Identifier (ST1), the version, and the target namespace. These values are compared to the grid in the **Envelopes** page (under **Transaction Set Settings** section) of the agreement properties (if an agreement is defined) or the fallback agreement properties (if no agreement is defined):<br /><br /> -   If there is a matching row, then the values contained in the matching row are used for the GS header.<br />-   If there is no match, but a default row is defined, all the GS data elements except GS01 are populated from the default row. GS01 is dynamically determined based on the value of ST1.<br />-   If there is no matching row, and no default row, the message is suspended. **Note:**  For a group to be unique from other groups, not all of these values can be the same as those for another group. <br /><br /> If no agreement is defined, then the GS data elements are populated from the fallback agreement properties.|  
  
### Sources for EDIFACT Envelope Values  
 The following table shows where the EDI send pipeline gets the information it needs for each part of an EDIFACT envelope:  
  
|Header|Source|  
|------------|------------|  
|Service String Advice (UNA)|-   EdiOverride context properties (if `EdiOverride.OverrideEdiHeader` is true).<br />-   If an agreement is defined, UNA segment definitions from **Charset and Separators** page in the one-way agreement properties in the **Agreement Properties** dialog box.<br />-   If no agreement is defined, UNA segment definitions from **Charset and Separators** page in the **EDIFACT Fallback Settings** dialog box.|  
|Interchange Control Header (UNB)|-   EdiOverride context properties (if `EdiOverride.OverrideEdiHeader` is true).<br />-   If an agreement is defined, UNB segment definitions from different pages under the **Interchange Settings** section in the one-way agreement properties in the **Agreement Properties** dialog box.<br />-   If no agreement is defined, UNB segment definitions from different pages under the **Interchange Settings** section in the **EDIFACT Fallback Settings** dialog box.|  
|Functional Group Headers (UNG)|-   EdiOverride context properties (if `EdiOverride.OverrideEdiHeader` is true).<br />-   If an agreement is defined, UNG and UNH segment definitions from the **Envelopes** page (under **Transaction Set Settings** section) in the one-way agreement properties in the **Agreement Properties** dialog box<br />-   If no agreement is defined, UNG and UNH segment definitions from the **Envelopes** page (under **Transaction Set Settings** section) in the one-way agreement properties in the **Agreement Properties** dialog box in the **EDIFACT Fallback Settings** dialog box<br /><br /> If an agreement is defined, the values for the UNG data elements are determined based upon the combination of the Message Type (UNH2.1), the Message Release Number (UNH2.3), the Assigned Code (UNH2.5), the version, and the target namespace. **Note:**  For a group to be unique from other groups, not all of these values can be the same as those for another group.|  
  
### Applying Transaction Set Header and Trailer Segments  
 An XML transaction set being serialized into an outgoing EDI interchange should have a transaction set header and trailer. However, the EDI Assembler will process the message if it does not have a transaction set header or trailer. Transaction set header and trailer segments in X12 and EDIFACT schemas are optional for XML transaction sets. If a transaction does not have a header or trailer, the EDI Assembler in the EDISend or AS2EDISend send pipeline will add transaction set header and trailer values to it. These values will be based on mappings or calculations. The EDI Assembler will do this for interchange XML (a preserved batch), batched transaction set XML, and transaction set XML.  
  
 If mapping causes a validation error, the XML transaction set or interchange XML is suspended with an appropriate error in the event viewer, such as invalid length or data type, or invalid Control Agency Code.  
  
####  <a name="BKMK_X12"></a> X12 Transaction Set Header and Trailer Segments  
 For X12-encoded transaction sets that do not have header and trailer segments, the EDI Assembler will set ST and SE segments to the following:  
  
|Header/Footer Segment|Value|  
|----------------------------|-----------|  
|ST01 (Transaction Set Identifier Code)|Mapped to the last three characters of the RootNode name from the incoming XML transaction set. For example, "855" from "X12_00401_855". For HIPAA Claims that have a TS Identifier Code of 837P, 837D, or 837I, "837" is used.|  
|ST02 (Transaction Set Control Number)|The value of `EdiOverride.ST02` (if `EdiOveride.OverrideEdiHeader` is true,) or mapped to the value of the **Transaction set control number (ST02)** in the **Local Host Settings** page (under **Interchange Settings**) of the one-way agreement tab in the **Agreement Properties** dialog box.<br /><br /> A new or incremented control number is applied regardless of the setting of the **Apply New ID** property.|  
|ST03 (Version identifier)|Mapped to the value of ST03 from the incoming XML transaction set. For example, “005010X218” for a 5010 HIPAA 820 document (Payroll deduction). ST03 is validated against the schema that is used to validate the transaction set. **Note:**  ST03 is mandatory for all HIPAA version 5010 transactions except for 835.|  
|SE01 (Number of Included Segments)|Set to the total number of segments in the transaction set, including the ST and SE segments.|  
|SE02 (Transaction Set Control Number)|Mapped to the value of ST02 in the transaction set.|  
  
 Other data elements in the transaction set header, such as ST03, are optional and so are not valued in the generated segments.  
  
####  <a name="BKMK_EDIFACT"></a> EDIFACT Transaction Set Header and Trailer Segments  
 For EDIFACT-encoded transaction sets that do not have header and trailer segments, the EDI Assembler will set UNH and UNT segments to the following:  
  
|Header/Footer Segment|Value|  
|----------------------------|-----------|  
|UNH01 (Message Reference Control Number)|The value of `EdiOverride.UNH1` (if `EdiOverride.OverrideEdiHeader` is true,) or mapped to the value of **Reference Number (UNH1)** in the **Local Host Settings** page (under **Interchange Settings**)of the one-way agreement tab in the **Agreement Properties** dialog box. A new or incremented control number is applied regardless of the setting of the **Apply New ID** property.|  
|UNH2.1 (Message Type)|Mapped to the last six characters of the RootNode name from the incoming XML transaction set. For example, "INVOIC" from "EFACT_D96A_INVOIC".|  
|UNH2.2 (Message Version Number)|Mapped to the seventh character of the RootNode name from the incoming XML transaction set. For example, "D" from "EFACT_D96A_INVOIC".|  
|UNH2.3 (Message Release Number)|Mapped to the eighth, ninth, and tenth characters of the RootNode name from the incoming XML transaction set. For example, "96A" from "EFACT_D96A_INVOIC".|  
|UNH2.4 (Control Agency Coded)|Always mapped to string ‘UN’.|  
|UNT01 (Number of Included Segments)|Set to the total number of segments in the transaction set, including the UNH and UNT segments.|  
|UNT02 (Message Reference Control Number)|Mapped to the value of **Reference Number (UNH1)** in the **Local Host Settings** page (under **Interchange Settings**)of the one-way agreement tab in the **Agreement Properties** dialog box|  
  
 Other data elements in the UNH transaction set header, such as UNH3 to UNH6, are optional and so are not valued in the generated segments. If any of these fields are required, you must set them to a value in the incoming XML transaction set.  
  
### Additional Processing on Envelope of an Outgoing Message  
 The EDI send pipeline performs the following processing on the envelope of an outgoing message.  
  
#### Control Numbers  
 The EDI send pipeline will enter an interchange control number, a group control number, and a transaction set control (or reference) number into the envelope segments of each outgoing interchange. These numbers are shown in the following table:  
  
|Control Number|X12 Field|EDIFACT Field|  
|--------------------|---------------|-------------------|  
|Interchange control number|ISA13|UNB5|  
|Group control number|GS6|UNG5|  
|Transaction set control number (X12)<br /><br /> Transaction set reference number (EDIFACT)|ST2|UNH1|  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will set the interchange control number for the next interchange sent based on the range of values that you entered in the **Interchange control number (ISA13)** property on the **Local Host Settings** page (under **Interchange Settings**) of the one-way agreement tab in the **Agreement Properties** dialog box. It will increment this number for each subsequent interchange, until the maximum value is reached.  
  
 If the interchange control number is specified using the EdiOverride context properties, the value specified will be used for this interchange and will not affect the interchange control number specified in agreement.  
  
> [!NOTE]
>  The group control number in EDIFACT is only incremented if the **Apply UNG segments** property in the **Envelopes** page of the EDIFACT agreement properties is selected. The second field (reference number) is incremented; the prefix and suffix fields are not incremented. Transaction set control numbers are only incremented if the **Apply new ID** property is selected.  
  
> [!NOTE]
>  In a preserved batch interchange, you can create a custom interchange control number using the message enrichment sample. For more information, see [Message Enrichment Sample (BizTalk Server Sample)](../core/message-enrichment-sample-biztalk-server-sample.md).  
  
 If no agreement is defined, the numbers are taken from the same pages in the fallback agreement. The send pipeline stores the last-used control number, and then enters an incremented number for the next interchange, group, and transaction set.  
  
> [!NOTE]
>  If any control number reaches the maximum value of the specified range, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will raise an error and suspend the interchange. You can manually reset the control number, or configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to automatically reset to the lower limit, in the **Local Host Settings** page in the **Agreement Properties** dialog box for both X12 and EDIFACT messages.  
> 
> [!NOTE]
>  Control numbers are saved in the dbo.EdiSequenceNumbers table of the BizTalk MessageBox database. You should manage this database table by purging the control numbers from the table or archiving the control numbers, as appropriate.  
  
 In EDIFACT, the control numbers consist of alphanumeric values. The following formats are supported:  
  
- Numbers (for example, "1")  
  
- PrefixNumbersSuffix (for example, "WA1A")  
  
- PrefixNumbers (for example, "AA1")  
  
- NumbersSuffix (for example, "1AA")  
  
  In these formats, the number characters can be from "0" to "9", and the prefix and suffix characters can be any characters other than numbers. Only the number will be incremented to reach the maximum value.  
  
#### Count of segments  
 For each transaction set in an interchange, the EDI send pipeline will verify the count of segments in the transaction set, as indicated in the SE01 data element for X12 and the UNT01 data element for EDIFACT. If the value of the appropriate data element does not match the actual count, the send pipeline will update the count to reflect the actual number of segments. The transaction set will not be rejected because of an erroneous count. The update of the count will be logged in a warning in the event viewer. This does not apply to the processing of preserved batches.  
  
## Additional Steps in Serializing an EDI Interchange  
 The EDI send pipeline also performs the following steps during serializing.  
  
### Serializing the Release Indicator  
 During the serializing of an EDIFACT messages, the EDI send pipeline will insert any required release indicator into the EDI interchange. It is assumed that the intermediate XML routed to the send pipeline does not include data that is escaped. For example, if a release indicator is present in the XML data routed to the send pipeline, the send pipeline will add another release indicator before the existing release indicator in order to escape it.  
  
 The release indicator will not be included in EDI validation. The EDI send pipeline will not include the release indicator when it computes length restrictions.  
  
### Adding Trailing Zeroes to Meet Implied Decimal Requirements  
 If the EDI Assembler encounters a number that has an insufficient number of digits after the decimal point, it will add trailing zeroes after the decimal point to meet implied decimal requirements. For example, if the EDI Assembler encounters the number "4.5" when the number should have the format N2, the Assembler will change the number to "4.50".  
  
### Replacing Separators in Payload Data  
 If the data in the outbound message contains characters that are also configured as data, segment or component separators, the EDI send pipeline can replace these characters. For example, if the message contains a value of “test*data” and the data element separator is configured as ‘\*’, this may cause parsing problems on the receiving system.  
  
 The EDI send pipeline can be configured to replace this character by enabling the **Replace separators in payload with** property and specifying a replacement character. This property is located in the **Charset and Separators** page in the one-way agreement tab of the **Agreement Properties** dialog box.  
  
### Transform HIPAA Records Based on Trigger Fields  
 If the outbound document is a HIPAA transaction set, the EDI Assembler will transform any unique XML record that contains a trigger field into the matching generic EDI segment (see [HIPAA Schema Trigger Field Annotations](../core/hipaa-schema-trigger-field-annotations.md)). This is accomplished by dropping the suffix of the XML record name after the “_” character.  
  
 For example, both the elements <N1_PayerIdentification_TS835W1_1000A> and <N1_PayeeIdentification_TS835W1_1000B> will become N1 segments.  
  
## See Also  
 [How BizTalk Server Sends EDI Messages](../core/how-biztalk-server-sends-edi-messages.md)