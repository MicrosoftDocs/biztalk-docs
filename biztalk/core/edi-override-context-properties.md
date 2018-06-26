---
title: "EDI Override Context Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d78cd56f-1e34-4503-8ee1-93b52137097f
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# EDI Override Context Properties
The message context properties in the EdiOverride global property schema can be used to override the EDI envelope values at runtime. These message context properties are defined in edi-properties.xsd in the Microsoft.BizTalk.Edi.BaseArtifacts assembly. The namespace for the properties is `http://schemas.microsoft.com/BizTalk/2006/edi-properties`.  
  
 The EdiOverride context properties are also available in an orchestration, as long as a reference to the Microsoft.BizTalk.Edi.BaseArtifacts assembly has been added to the orchestration project.  
  
|Name|Type|Description|  
|----------|----------|-----------------|  
|OverrideEDIHeader|boolean|If true, the EDI Send pipeline will attempt to construct the EDI envelope using the values in the EdiOverride property collection.|  
|ISA01|string|The Authorization Information Qualifier (X12)|  
|ISA02|string|The Authorization Information (X12)|  
|ISA03|string|The Security Information Qualifier (X12)|  
|ISA04|string|The Security Information (X12)|  
|ISA05|string|The Interchange Sender Qualifier (X12)|  
|ISA06|string|The Interchange Sender ID (X12)|  
|ISA07|string|The Interchange Receiver Qualifier (X12)|  
|ISA08|string|The Interchange Receiver ID (X12)|  
|ISA09|string|The Interchange Date (X12)<br /><br /> This field should contain the actual date value instead of the date format.|  
|ISA10|string|The Interchange Time (X12)<br /><br /> This field should contain the actual time value instead of the date value.|  
|ISA11|string|The Interchange Control Standards identifier (X12)|  
|ISA12|string|The Interchange Control Version Number (X12)|  
|ISA13|string|The Interchange Control Number (X12)<br /><br /> If the Interchange Control Number is overridden, the corresponding Interchange Trailer segment (IEA) will be set to match the specified value.|  
|ISA14|string|The Acknowledgement Requested (X12)|  
|ISA15|string|The Test Indicator (X12)|  
|ISA16|string|The Component Element separator (X12)|  
|GS01|string|The Functional Identifier Code (X12)|  
|GS02|string|The Application Sender’s Code (X12)|  
|GS03|string|The Application Receiver’s Code (X12)|  
|GS04|string|The Date (X12)<br /><br /> This field should contain the actual date value instead of the date format.<br /><br /> This value should be in either CCYYMMDD or YYMMDD format. The date provided will be used even if the date is provided in a format different than the one selected in Party properties.|  
|GS05|string|The Time (X12)<br /><br /> This field should contain the actual time value instead of the time format.<br /><br /> This value should be in HHMM, HHMMSS or HHMMSSdd format. The time provided will be used even if the time is provided in a format different than the one selected in Party properties.|  
|GS06|string|The Group Control Number (X12)<br /><br /> When the Group Control Number is overridden, the corresponding field in the GE segment will be set to match the value specified.|  
|GS07|string|The Responsible Agency Code (X12)|  
|GS08|string|The Version/Release/Industry Identifier Code (X12)|  
|ST02|string|The Transaction Set Control Number (X12)<br /><br /> If the Transaction Set Control Number is overridden, the corresponding field in the Transaction Set Trailer segment (SE) will be set to match this value.|  
|GenerateUNA|boolean|Determines if the EDI send pipeline will create a UNA segment for the outbound EDIFACT document.<br /><br /> If OverrideEdiHeader is true, and GenerateUNA is true, a UNA segment will be generated. If OverrideEdiHeader is true, and Generate UNA is false, no UNA segment will be generated.<br /><br /> The values for the UNA segment are determined in the following order:<br /><br /> -   EdiOverride context properties, if all UNA properties are present.<br />-   If not all context properties are present, and Generate UNA segment is checked in Party properties, a combination of context properties and party properties.<br />-   If not all context properties are present, and Generate UNA segment is unchecked in Party properties, a combination of context properties and standard UNA values **Note:**  This field has no effect if OverrideEdiHeader is false.|  
|UNA1|string|The Component Data Element Separator (EDIFACT)|  
|UNA2|string|The Data Element Separator (EDIFACT)|  
|UNA3|string|The Decimal Mark (EDIFACT)|  
|UNA4|string|The Release Character (EDIFACT)|  
|UNA5|string|The Repetition Separator (EDIFACT)|  
|UNA6|string|The Segment Terminator (EDIFACT)|  
|UNA6Suffix|string|The Segment Terminator Suffix (EDIFACT)|  
|UNB1_1|string|The Syntax Identifier (EDIFACT)|  
|UNB1_2|string|The Syntax Version Number (EDIFACT)|  
|UNB10|string|The Communications Agreement ID (EDIFACT)|  
|UNB11|string|The Test Indicator (EDIFACT)|  
|UNB2_1|string|The Sender Identification (EDIFACT)|  
|UNB2_2|string|The Partner Identification Code Qualifier (EDIFACT)|  
|UNB2_3|string|The Address for Reverse Routing (EDIFACT)|  
|UNB3_1|string|The Recipient Identification (EDIFACT)|  
|UNB3_2|string|The Partner Identification Code Qualifier (EDIFACT)|  
|UNB3_3|string|The Routing Address (EDIFACT)|  
|UNB4_1|string|The Date (EDIFACT)<br /><br /> This field should contain the actual date value instead of the date format.|  
|UNB4_2|string|The Time (EDIFACT)<br /><br /> This field should contain the actual time value instead of the time format.|  
|UNB5|string|The Interchange Control Reference (EDIFACT)<br /><br /> When the Interchange Control Reference is overridden, the control number in the Interchange Trailer segment (UNZ) will be set to match the specified value.|  
|UNB6_1|string|The Recipient’s Reference/Password (EDIFACT)|  
|UNB7|string|The Application Reference (EDIFACT)|  
|UNB8|string|The Processing Priority Code (EDIFACT)|  
|UNB9|string|The Acknowledgement Request (EDIFACT)|  
|GenerateUNG|boolean|Determines if the EDI send pipeline will create a UNG segment for the outbound EDIFACT document.<br /><br /> If OverrideEdiHeader is true, and GenerateUNG is true, a UNG segment will be generated. If OverrideEdiHeader is true and Generate UNG is false, no UNG segment will be generated.<br /><br /> The values for the UNG segment are determined in the following order:<br /><br /> -   EdiOverride context properties, if all UNG properties are present.<br />-   If not all context properties are present, and Generate UNG segment is checked in Party properties, a combination of context properties and party properties.<br />-   If not all context properties are present, and Generate UNG segment is unchecked in Party properties, a combination of context properties and standard UNA values **Note:**  This field has no effect if OverrideEdiHeader is false.|  
|UNG1|string|The Message Group Identification (EDIFACT)|  
|UNG2_1|string|The Application Sender Identification (EDIFACT)|  
|UNG2_2|string|The Identification Code Qualifier (EDIFACT)|  
|UNG3_1|string|The Application Recipient Identification (EDIFACT)|  
|UNG3_2|string|The Identification Code Qualifier (EDIFACT)|  
|UNG4_1|string|The Date of Preparation (EDIFACT)<br /><br /> This field should contain the actual date value instead of the date format.|  
|UNG4_2|string|The Time of Preparation (EDIFACT)<br /><br /> This field should contain the actual time value instead of the time format.|  
|UNG5|string|The Group Reference Number (EDIFACT)<br /><br /> If the Group Reference Number is overridden, the corresponding field in the Group Trailer segment (UNE) will be set to match the specified value.|  
|UNG6|string|The Controlling Agency Coded (EDIFACT)|  
|UNG7_1|string|The Message Version Number (EDIFACT)|  
|UNG7_2|string|The Message Release Number (EDIFACT)|  
|UNG7_3|string|The Association Assigned Code (EDIFACT)|  
|UNG8|string|The Application Password (EDIFACT)|  
|UNH1|string|The Message Reference Number (EDIFACT)<br /><br /> When the Message Reference Number is overridden, the corresponding field in the Message Trailer segment (UNT) will be set to match this value.|  
  
## EDIOverride Context Property Usage  
 If the **OverrideEdiHeader** context property is true, the values specified in the EDIOverride context properties will be used to create the EDI envelope for the outbound message. If no value is specified for an EDIOverride context property, the corresponding Party or Global property will be used.  
  
 Values specified for EDIOverride context properties must be valid in accordance with the X12 or EDIFACT standards and any service schema extensions.  
  
- Fields should contain valid values for that field type, including extensions to the service schema.  
  
- Control numbers must be of a valid type, but do not need to be next in sequence with existing Party settings.  
  
- Date and time fields should contain date and time values, and be valid according to the relevant EDI standard even if the value format does not match the format defined in Party settings.  
  
  Some EDIOverride context properties are only supported when the message being sent by the EDI Send pipeline is a single transaction or a batch. The following table lists the supported context properties for each message type:  
  
|EDI transaction being sent|Supported EDIOverride context properties|  
|--------------------------------|----------------------------------------------|  
|Single transaction set|-   All ISAs<br />-   All GSs<br />-   ST02<br />-   GenerateUNA<br />-   All UNAs<br />-   All UNBs<br />-   GenerateUNG<br />-   All UNGs<br />-   UNH1|  
|Batch transaction set published by the batching orchestration or Batch-in-Batch-Out transaction set published by the EDI Receive pipeline|-   All ISAs<br />-   GS04<br />-   GS05<br />-   GenerateUNA<br />-   All UNAs<br />-   All UNBs<br />-   GenerateUNG<br />-   UNG4.1<br />-   UNG4.2|  
  
 EDIOverride context properties can also be applied to messages that will be batched, however the batching orchestration only supports the ST01 and UNH1 EDIOverride context properties.  
  
## See Also  
 [Developing and Configuring BizTalk Server EDI Solutions](../core/developing-and-configuring-biztalk-server-edi-solutions.md)