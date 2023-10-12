---
description: "Learn more about: Overriding EDI Headers"
title: "Overriding EDI Headers"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Overriding EDI Headers
When sending an EDI-encoded interchange, the EDI envelope applied to the message is normally based upon the EDI properties of the receiving agreement, or the fallback agreement properties. However it is often useful to set the EDI envelope properties based on runtime generated values.  
  
 In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can use the EdiOverride context properties to specify the values used to generate the EDI envelope on outbound documents.  
  
## Using EdiOverride Context Properties  
 The EdiOverride context properties provide a way to override all, or part, of the values used to generate the EDI envelope. The EDI send pipeline will use EdiOverride context property that contains a valid value to construct the envelope. If a property is not populated, the pipeline will use the value specified in agreement properties or fallback agreement properties, if an agreement is not defined. If a property contains an invalid value, the pipeline will suspend the message and report a validation error.  
  
> [!NOTE]
>  The values specified in the EdiOverride collection are only used if the `EdiOverride.OverrideEdiHeader` property is written into the context of a message and contains a value of “True”.  
>   
>  The default value is not set.  
  
### EdiOverride properties for X12 Envelope Values  
 The following table shows the EdiOverride context properties and the corresponding X12 envelope header:  
  
|Header|Properties|  
|------------|----------------|  
|Interchange Control Header (ISA)|ISA01, ISA02, ISA03, ISA04, ISA05, ISA06, ISA07, ISA08, ISA09, ISA10, ISA11, ISA12, ISA13, ISA14, ISA15, ISA16|  
|Functional Group Headers (GS)|GS01, GS02, GS03, GS04, GS05, GS06, GS07, GS08|  
|Transaction Set Header|ST02|  
  
### EdiOverride properties for EDIFACT Envelope Values  
 The following table shows the EdiOverride context properties and the corresponding EDIFACT envelope segment:  
  
|Segment|Properties|  
|-------------|----------------|  
|Service String Advice (UNA)|UNA1, UNA2, UNA3, UNA4, UNA5, UNA6, UNA6Suffix|  
|Interchange Control Header (UNB)|UNB1_1, UNB1_2, UNB2_1, UNB2_2, UNB2_3, UNB3_1, UNB3_2, UNB3_3, UNB4_1, UNB4_2, UNB5, UNB6_1, UNB7, UNB8, UNB9, UNB10, UNB11|  
|Functional Group Headers (UNG)|UNG1, UNG2_1, UNG2_2, UNG3_1, UNG3_2, UNG4_1, UNG4_2, UNG5, UNG6, UNG7_1, UNG7_2, UNG7_3, UNG8|  
|Message Header (UNH)|UNH1|  
  
 Since the UNA and UNG EDIFACT segments are optional, the GenerateUNA and GenerateUNG properties can be used to determine if these headers are generated, regardless of the **Apply UNA segment** agreement setting. The following tables show the values that result in generation of these segments:  
  
|GenerateUNA context property|Apply UNA segment agreement setting|Engine behavior|  
|----------------------------------|-----------------------------------------|---------------------|  
|TRUE|CHECKED|Generate UNA|  
|TRUE|UNCHECKED|Generate UNA|  
|FALSE|CHECKED|Do not generate UNA|  
|FALSE|UNCHECKED|Do not generate UNA|  
|Not present (OverrideEDIHeader is false)|CHECKED|Generate UNA|  
|Not present (OverrideEDIHeader is false)|UNCHECKED|Do not generate UNA|  
  
|GenerateUNG context property|Apply UNG segments agreement setting|Engine behavior|  
|----------------------------------|------------------------------------------|---------------------|  
|TRUE|CHECKED|Generate UNG|  
|TRUE|UNCHECKED|Generate UNG|  
|FALSE|CHECKED|Do not generate UNG|  
|FALSE|UNCHECKED|Do not generate UNG|  
|Not present (OverrideEDIHeader is false)|CHECKED|Generate UNG|  
|Not present (OverrideEDIHeader is false)|UNCHECKED|Do not generate UNG|  
  
### Group envelopes  
 Group envelopes present a special challenge, as the interchange can have more than one group present. To address this, the EDI send pipeline can either apply the envelope to all groups in the interchange, or apply the envelope to the only group in the interchange.  
  
 For single transactions, all GS or UNG fields can be overridden, for batch interchanges only the following fields can be overridden:  
  
-   GS04  
  
-   GS05  
  
-   UNG4_1  
  
-   UNG4_2  
  
### Batching  
 Overriding the transaction set control number for batched messages is handled by the Batching orchestration. The following properties can be written to the context of any message that will be batched to override the transaction set control number:  
  
-   ST02 (for X12 messages)  
  
-   UNH1 (For EDIFACT messages  
  
> [!NOTE]
>  If multiple incoming messages contain the same control number in the same group, messages with duplicate numbers will be suspended.  
  
> [!NOTE]
>  Do not promote the EdiOverride context properties ISA, UNA, GS, or UNG for messages that are to be batched. If you need to override these properties, promote them on the output message of the batch orchestration before sending to the EDI send pipeline.  
  
### Delimiter collision  
 Delimiters, such as the UNA headers, must contain a unique value for each field. When overriding delimiter values, such as the UNA headers, you must ensure that each delimiter value is unique not only within the values you override, but also among any delimiter values used from the agreement or fallback agreement settings.  
  
 For example, if you override UNA1, UNA2, and UNA4, and UNA3, UNA5, UNA6 and UNA6Suffix come from agreement properties, each property must contain a unique value compared to the others.  
  
## See Also  
 [How BizTalk Server Sends EDI Messages](../core/how-biztalk-server-sends-edi-messages.md)
