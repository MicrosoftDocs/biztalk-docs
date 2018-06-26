---
title: "EDI Type (Data Element) Validation | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cd53685f-a49c-41c8-813e-29700fc0b62b
caps.latest.revision: 19
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# EDI Type (Data Element) Validation
The EDI receive pipeline and EDI send pipeline perform EDI validation on transaction-set data elements. This validation is configured for all messages from or to a specific party, through that party's agreement properties on the **Validation** page (under the **Transaction Set Settings** section for either X12 or EDIFACT agreements). If the **EDI Type Validation** property is not selected in the **Validation** page, the data validations described in this topic will not be performed.  
  
 EDI type validation is enabled for incoming as well as outgoing messages by selecting the **EDI type Validation** property in the **Validation** page of the bi-directional agreement tabs in the **Agreement Properties** dialog box. For both incoming and outgoing messages, this property is selected by default so that EDI validation is enabled by default.  
  
## Validation Checks  
 When the EDI receive pipeline or EDI send pipeline performs EDI validation, it validates the following:  
  
- Data types as defined by the EDI properties of the schema  
  
- Length restrictions  
  
- Empty data elements and trailing separators  
  
  > [!NOTE]
  >  This validation does not check code sets (enumerations) or min or max occurs.  
  
  **Character Sets**  
  
  To perform EDI data element validations, the EDI receive and send pipelines require the character set to be established as follows:  
  
- For EDIFACT, the character set is established in data element **UNB1** of the **Charset and Separators** page of the one-way agreement tab of the **Agreement Properties** dialog box or the **EDIFACT Fallback Settings** dialog box (if no agreement has been established).  
  
- For KEDIFACT, the character is established in data element **UNB1** of the **Charset and Separators** page of the one-way agreement tab of the **Agreement Properties** dialog box, as for EDIFACT. The value for the **UNB1.1** element must be set to `KECA`.  
  
- For X12, the character set is established for the message in the pipeline properties.  
  
  > [!NOTE]
  >  When the BizTalk runtime performs EDI validation of a message, it will use the X12 character set selected in the pipeline properties. However, validation of the properties entered in the pages of the **Agreement Properties** dialog box is performed using the character set selected in the **Charset and Separators** page of that dialog box. During runtime, the pipeline ignores the value of the X12 character set property **Charset and Separators** page of the **Agreement Properties** dialog box. If these two settings are not the same (i.e., the X12 character set property in the **Agreement Properties** dialog box is set to **Extended** while the X12 character property in the pipeline properties is set to **Basic**), message validation errors could result.  
  
  **Data Type Validation**  
  
  For X12, the following EDI data types are annotated in schema for validation by the Disassembler/Assembler components in the Receive or Send Pipelines: Numeric, Decimal, Identifier, String, Date, Time, Binary, and Composite.  
  
  For EDIFACT, the following EDI data types are annotated in schema for validation by the Disassembler/Assembler components in the Receive or Send Pipelines: Alphabetic, Numeric, Identifier, String, and Composite.  
  
  **Length Restrictions**  
  
  For both X12 and EDIFACT, elements or sub-elements must be validated for length (minimum and maximum) requirement. Length is defined as the number of character positions used. Length does not include signs and decimal notations.  
  
> [!NOTE]
>  For the X12_AN string data type, leading spaces are preserved and trailing spaces are allowed in any segment to satisfy the minimum length requirement.  
  
 For KECA, length is interpreted as the number of bytes. For example, if the length is defined as three, the element or sub-element can include either three one-byte characters or the combination of one two-byte character and one one-byte character.  
  
 **Empty Data Elements and Trailing Separator Validation**  
  
 For X12, data elements marked as mandatory cannot be empty in an instance if the segment is present. If the data element is composite at least one component data element must be valued.  
  
 For EDIFACT, non-valued and conditional data elements (and sub-components) may be excluded; however, the separator is retained.  
  
 Trailing separators are not required for either X12 or EDIFACT, but are recommended.  
  
## When EDI Type Validation Is Disabled  
 If you deactivate the EDI type validation, the EDI receive pipeline or EDI send pipeline will process data elements that have errors checked by the EDI type validation without suspending the message being processed.  
  
> [!NOTE]
>  EDI structural validation is performed even if the EDI type validation is disabled. An interchange that fails the basic structural validations will be suspended, even if the EDI Type validation is disabled.  
  
 Some of the errors that will be processed without causing the message to be suspended are:  
  
- An unexpected/undefined transaction set  
  
- Unexpected/undefined data at the segment/loop and data element level  
  
- Optionality (min and max occurs) at the segment/loop and data element level  
  
- Length (min/max) violation at the data element level (data with length exceeding the maximum level or below the minimum level)  
  
- Data type mismatch at the data element level (except for the ID data type, which has its own control)  
  
- Invalid enumeration list at the data element level.  
  
  If EDI type validation is disabled on the receive side, but enabled on the send side, the EDI send pipeline will not be able to reprocess the XML produced by the receive pipeline into a valid EDI file if the XML file contains errors. As a result, the send pipeline will generate an error.  
  
  If EDI Type validation is disabled, the EDI receive pipeline or send pipeline will handle errors as follows:  
  
|||  
|-|-|  
|Unexpected Data|Action|  
|Unexpected/undefined transaction set|The EDI receive or send pipeline will accept a transaction set even if a schema for it has not been deployed|  
|Unexpected segment/record|The receive pipeline will generate a tag with the appropriate prefix: \<UnexpectedSegment_%SegmentID%\>.<br /><br /> The send pipeline will use the first one to three characters of the XML Tag name as the segment name.|  
|Unexpected simple data element|The receive pipeline will generate an XML tag with a prefix, segment identifier, and index representing the position of the data element in the segment: <UnexpectedDataElement_%FieldName%.|  
|Unexpected composite data element|The receive pipeline will generate an XML tags with prefix, segment identifier, and index representing the position of the data element in the segment: <UnexpectedCompositeDataElement_%FieldName%.|  
|Missing required data|The pipeline will treat the data as optional.|  
|Data element length violation|The pipeline will treat the invalid data element length as valid (min = 0 and max = unbounded).|  
|Invalid enumeration value in the instance (applicable to the ID data type)|The pipeline will ignore the error and continue processing.|  
|‘Max’ repletion violation in the instance|The pipeline will treat such repetitive data as valid (min occurs = 0 and max occurs = unbounded).|  
  
 **Error Reporting**  
  
 When EDI type validation is turned off, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] does not report errors in the Event Viewer, but reports a warning. In addition, the acknowledgment reports an ‘Accept’ back to the source party, setting AK501 and AK901 as “E” in an X12 997 or UCI.4, UCM.3, and UCF.4 as “7” in an EDIFACT CONTRL. As a result, any chance of rectification in future transmissions will be eliminated. However, receivers of the message will have an opportunity to salvage the document via manual intervention rather than the message being rejected or suspended. Also, the `Edi.ErrorsInTransactionSet` context property will be promoted if any of these errors are encountered by the EDI receive pipeline. This property will be promoted as "True" if EDI or Extended validation errors are encountered. If not errors are encountered, the property will be promoted as "False".  
  
 If the receive or send pipeline encounters unexpected data, it will report the error at the parent level and ignore child level errors, as follows:  
  
|||  
|-|-|  
|Unexpected Data|Action|  
|Unexpected transaction set|The acknowledgment reports this error and ignores subsequent errors at the segment/loop and data element level|  
|Unexpected segment/loop|The acknowledgment reports this error and ignores errors at the data element level.|  
|Unexpected data element|The acknowledgment reports this error and ignores compound errors relating to properties like ID, length, occours, etc) and errors relating to composite data element fields (if applicable).|  
  
## See Also  
 [EDI Message Validation](../core/edi-message-validation.md)   
 [Extended (BTS-XSD) Validation](../core/extended-bts-xsd-validation.md)