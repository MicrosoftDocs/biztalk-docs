---
title: "Schema Known Issues | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "known issues, schemas"
  - "schemas, known issues"
ms.assetid: 17651462-baa9-448a-954c-c09e70640f17
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Schema Known Issues
This section contains useful information that may help you avoid schema errors.  
  
## MCF_21_GLO_DEF.xsd schema  
 In the templates\schemas\2.1 folder, schema MCF_21_GLO_DEF.xsd is not a part of the Common231 project.  
  
## Miscellaneous errors can result from undeployed schemas  
 If you are unable to identify an error in parsing or serializing, verify that you have deployed property schemas and common schemas (MSH/ACK). Undeployed property schemas and common schemas can cause miscellaneous errors.  
  
## If the Starter Project is installed, but the HL7 2.X schemas are not installed, running the Schema Wizard generates an error  
 If you run a custom installation of [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) in which you install the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Starter Project, but do not install the HL7 2.X schemas, and then attempt to run the Schema Wizard, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] will generate an error. The solution to this is to run the Custom installation process again to install the HL7 2.X schemas.  
  
## MSH9.1 enumeration list needs to be updated  
 The MSH_25_GLO_DEF schema installed by [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] upon setup does not contain the full enumeration lists for MSH9.1 (MessageType) and MSH9.2 (EventTrigger), as contained in the HL72.X standard. The following table lists message type and trigger event values that you will have to add to their associated table if you want to use a schema whose message type contains the value. For instance, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] will not process a QBP^Z99 message until you add "QBP" to the enumeration for Table76 in MSH_25_GLO_DEF, and it will not process an QBP^Z99 message until you add "Z99" to the enumeration for Table3 in MSH_25_GLO_DEF.  
  
 To add a value to either the MSH9.1 or MSH9.2 enumeration, see the "To add an enumeration value to a message-header schema" procedure in [Extending Enumerations](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md).  
  
|Field/Table|Value to be added to enumeration|  
|------------------|--------------------------------------|  
|MessageType/Table76|ARD, RDO, RRO|  
|TriggerEvent/Table3|K11, K13, K15, MFA, O22, Q11, Q13, Q15, Q26, Q27, Q28, Q29, R0R, Z73, Z74, Z75, Z76, Z77, Z78, Z79, Z80, Z81, Z82, Z83, Z84, Z85, Z86, Z87, Z88, Z89, Z90, Z91, Z92, Z93, Z94, Z95, Z96, Z97, Z98, Z99|  
|MessageStructure/Table354|ARD_A19, ORL_O22|  
  
## BTAHL7 does not support schemas with an ambiguous structure  
 The BTAHL7 engine cannot process message instances conforming to HL7 schemas that have an ambiguous structure. An ambiguous schema structure is one that is not completely defined by the HL7 standard. Such schemas include those for message types CSU, OMD, ORD, and SUR.  
  
## BTAHL7 will return a segment sequence error for some messages  
 BTAHL7 cannot process messages conforming to the schemas listed below. Parsing of the body of these messages will fail, resulting in the following error: "Segment sequence error (Invalid segment found after this segment)." The affected Segment IDs in the messages are listed below. The affected sequence numbers for all these errors is "2".  
  
|Version|Message Type|Trigger Event|Segment ID|  
|-------------|------------------|-------------------|----------------|  
|V2.3|CSU|C09|ORC_CommonOrderSegment|  
|V2.3|CSU|C10|ORC_CommonOrderSegment|  
|V2.3|CSU|C11|ORC_CommonOrderSegment|  
|V2.3|CSU|C12|ORC_CommonOrderSegment|  
|V2.3|SUR|P09|PSH_ProductSummaryHeader|  
|V2.3.1|CSU|C09|ORC_CommonOrderSegment|  
|V2.3.1|CSU|C10|ORC_CommonOrderSegment|  
|V2.3.1|CSU|C11|ORC_CommonOrderSegment|  
|V2.3.1|CSU|C12|ORC_CommonOrderSegment|  
|V2.3.1|SUR|P09|PSH_ProductSummaryHeader<br />Segment|  
|V2.4|CSU|C09|ORC_CommonOrder|  
|V2.4|CSU|C10|ORC_CommonOrder|  
|V2.4|CSU|C11|ORC_CommonOrder|  
|V2.4|CSU|C12|ORC_CommonOrder|  
|V2.4|OMD|O03|ORC_CommonOrder|  
|V2.4|ORD|O04|ORC_CommonOrder|  
|V2.4|SUR|P09|PSH_ProductSummaryHeader|  
|V2.5|CSU|C09|ORC_CommonOrder|  
|V2.5|CSU|C10|ORC_CommonOrder|  
|V2.5|CSU|C11|ORC_CommonOrder|  
|V2.5|CSU|C12|ORC_CommonOrder|  
|V2.5|OMD|O03|ORC_CommonOrder|  
|V2.5|ORD|O04|ORC_CommonOrder|  
|V2.5|SUR|P09|PSH_ProductSummaryHeader"|  
|V2.5|RDE|025|PSH_ProductSummaryHeader"|  
|V2.5|OUL|R24|PSH_ProductSummaryHeader"|  
|V2.5|OML|035|PSH_ProductSummaryHeader"|  
|V2.5|ORL|034|PSH_ProductSummaryHeader"|  
  
> [!NOTE]
>  The above list for version 2.5 is not exhaustive and may include additional message types that result in the "Segment Sequence Error."  
  
## BTAHL7 does not support some v2.3.1 schemas  
 The BTAHL7 setup program does not install the following v2.3.1 schemas:  
  
-   OMD_O01_231_GLO_DEF  
  
-   OMN_O01_231_GLO_DEF  
  
-   OMS_O01_231_GLO_DEF  
  
-   ORD_O02_231_GLO_DEF  
  
-   ORN_O02_231_GLO_DEF  
  
-   ORS_O02_231_GLO_DEF  
  
## See Also  
 [Known Issues](../../adapters-and-accelerators/accelerator-hl7/known-issues1.md)