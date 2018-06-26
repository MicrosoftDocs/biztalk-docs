---
title: "Configuring EDI Pipeline Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.edir2.edi.pipeline.properties"
ms.assetid: 1b6229b6-a8b0-4824-86bd-39021844c5a8
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring EDI Pipeline Properties
Pipeline properties are used in processing an incoming or outgoing EDI interchange when [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is unable to determine the agreement that the incoming or outgoing interchange resolves to. In some cases, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses the pipeline property to process the interchange; in others, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] use the fallback agreement. For more information, see [How Validation of an EDI Interchange Is Configured](../core/how-validation-of-an-edi-interchange-is-configured.md).  
  
 There are a few exceptions to this rule:  
  
- For X12, the character set used at runtime is determined by the pipeline property, even if the agreement has been determined. The character set described in the agreement is used only to validate agreement property settings.  
  
- For EDIFACT, if an incoming interchange does not have a UNA segment, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses the delimiters specified in the EfactDelimiters pipeline property, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] does not use the properties defined in the agreement the message resolves to or the fallback agreement.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
## EDI Pipeline Properties  
 The following properties can be set in EDI pipelines:  
  
|Property|Use|Values|Pipeline - Stage|  
|--------------|---------|------------|-----------------------|  
|AllowTrailingDelimiters|Generates trailing separators on the interchange received.|False (default)<br /><br /> True|EdiReceive- Disassemble<br /><br /> AS2EdiReceive -Disassemble<br /><br /> EdiSend - Assemble<br /><br /> AS2EdiSend - Assemble|  
|CharacterSet|Specifies the character set to be used during run-time validation of outgoing EDI interchanges.<br /><br /> This property is used for X12 processing only, not for EDIFACT.|UTF8 (default)<br /><br /> Basic<br /><br /> Extended|EdiReceive - Disassemble<br /><br /> AS2EdiReceive -Disassemble<br /><br /> EdiSend - Assemble<br /><br /> AS2EdiSend - Assemble|  
|ConvertToImpliedDecimal|For an incoming interchange, converts an EDI number that is specified with the format Nn into a base-10 numeric value in the intermediate XML in BizTalk Server.<br /><br /> This property is used for X12 processing only, not for EDIFACT.|False (default)<br /><br /> True|EdiReceive - Disassemble<br /><br /> AS2EdiReceive - Disassemble|  
|CreateXMLTagForTrailingSeparators|Creates empty XML tags for each of the trailing separators (if you have set **AllowTrailingDelimiters** to true).|False (default)<br /><br /> True|EdiReceive - Disassemble<br /><br /> AS2EdiReceive - Disassemble|  
|DetectMID|Enables the EDI Disassembler to parse multiple interchanges in a single message.|True (default)<br /><br /> False|EdiReceive - Disassemble<br /><br /> AS2EdiReceive - Disassemble|  
|EdiDataValidation|Enables EDI type (data elements) validation of outgoing EDI interchanges, including validation of field length, optionality, and repeat count in addition to EDI data element validation.|True (default)<br /><br /> False|EdiReceive - Disassemble<br /><br /> AS2EdiReceive - Disassemble<br /><br /> EdiSend - Assemble<br /><br /> AS2EdiSend - Assemble|  
|EfactDelimiters|Indicates the delimiters to be used in processing an incoming interchange. Used if an incoming interchange does not have a UNA segment.<br /><br /> The delimiters include the following:<br /><br /> -   UNA1 (Component data element separator)<br />-   UNA2 (Data element separator)<br />-   UNA3 (Decimal notation)<br />-   UNA4 (Release indicator)<br />-   UNA5 (Repetition separator)<br />-   UNA6 (Segment terminator) **Note:**  This property is used for EDIFACT processing only, not for X12.|0x3A, 0x2B, 0x2C, 0x3F, 0x20, 0x27 (defaults)|EdiReceive - Disassemble<br /><br /> AS2EdiReceive - Disassemble|  
IgnoreMessageEncoding|Specifies that the BatchMarker component will not set the EDI.EncodingType context property to \<X12\> or \<EDIFACT\>. This applies to custom pipelines when processing non-EDI messages.|False (default)<br /><br /> True|EdiReceive - ResolveParty<br /><br /> AS2EdiReceive - ResolveParty|  
|MaskSecurityInformation|Mask authorization/password security information in the context property of an incoming EDI interchange to prevent information disclosure. Applies to the ISA1, ISA2, ISA3, and ISA4 fields for X12 interchanges; and the UNB6 fields for EDIFACT interchanges.|True (default)<br /><br /> False|EdiReceive - Disassemble<br /><br /> AS2EdiReceive - Disassemble|  
|PreserveInterchange|Specifies that a batch received will be processed as a single unit.|False (default)<br /><br /> True|EdiReceive - Disassemble<br /><br /> AS2EdiReceive - Disassemble|  
|RouteAckOn2WayPort|Returns an EDI acknowledgment over the open connection of a two-way request-response receive port.|True (default)<br /><br /> False|EdiReceive - Disassemble<br /><br /> AS2EdiReceive - Disassemble|  
|UseDotAsDecimalSeperator|When set to True, the EDI receive pipeline uses a decimal notation of “.” instead of the decimal notation of the incoming document.|False (default)<br /><br /> True|EdiReceive – Disassemble<br /><br /> AS2EdiReceive - Disassemble|  
|UseIsa11AsRepetitionSeparator|Specifies that ISA11 is used as a Repetition separator instead of a Standard identifier. **Note:**  This property is used for X12 processing only, not for EDIFACT.|False (default)<br /><br /> True|EdiReceive - Disassemble<br /><br /> AS2EdiReceive - Disassemble|  
|XmlSchemaValidation|Enables extended (BTS-XSD) validation of outgoing EDI interchanges. This applies only if the schema has been customized with elements whose data type is not an EDI data type. These added elements are not be validated by EDI validation, so will be covered by extended validation.|False (default)<br /><br /> True|EdiReceive - Disassemble<br /><br /> AS2EdiReceive - Disassemble<br /><br /> EdiSend - Assemble<br /><br /> AS2EdiSend - Assemble|  
  
### To set a pipeline property  
  
1. In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the receive location or send port using the pipeline that you want to set properties for, and then click **Properties**.  
  
2. Click the ellipsis button (…) next to the pipeline that you want to set properties for.  
  
3. In the **Configure Pipeline** dialog box, enter the value for the property, and then click **OK**.  
  
## See Also  
 [How Validation of an EDI Interchange Is Configured](../core/how-validation-of-an-edi-interchange-is-configured.md)