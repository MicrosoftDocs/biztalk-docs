---
title: "Segment and Field | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "messages, segments"
  - "messages, fields"
  - "segments, messages"
ms.assetid: e68864e6-590c-47f3-8c9e-81831aec2642
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Segment and Field
A segment table defines an HL7 segment. Each segment definition follows the pattern shown below.  
  
|SEQ|LEN|DT|OPT|RP/#|TBL#|ITEM#|ELEMENT NAME|  
|---------|---------|--------|---------|------------|-----------|------------|------------------|  
|1|4|SI|O|||00104|Set ID - PID|  
|2|20|CX|B|||00105|Patient ID|  
|3|250|CX|R|Y||00106|Patient Identifier List|  
|4|20|CX|B|Y||00107|Alternate Patient ID - PID|  
|5|250|XPN|R|Y||00108|Patient Name|  
|..||||||||  
|..||||||||  
|37|80|ST|O|||01541|Strain|  
|38|250|CE|O|2|0429|01542|Production Class Code|  
  
 HL7 also includes text definitions for each field. The three-character segment tag and the sequence number uniquely identify each field within a segment. For example, in the case of the Patient Identification segment, the tag PID and the sequence number "5" uniquely identify the patient-name field. The XML encoding and interface documentation both use this convention to identify the fields in segments. The segment definition also includes the data type declaration for each field, as well as the table number that applies to coded elements.  
  
 In new versions, you can only add fields at the end of a segment, and you cannot remove fields. If an added field replaces the functionality of an existing field, the first field remains for backward compatibility. (This can be seen by the "B" in the optionally column above for PID.2 and PID.3.)  
  
 The following functions of [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) support these requirements:  
  
- [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] supports the standard segments for all HL7 versions from V2.1 on.  
  
- When you construct interface specifications and implement interfaces, you can label fields that are optional in the standard as either mandatory or not supported, based on functional requirements.  
  
- You can create Z segments where needed for localization.  
  
- You can redefine the semantics of fields or add fields to segments where needed for localization. Note that this falls under the heading of illegitimate localization. However, in some cases you need this functionality to support legacy interfaces or interfaces to legacy systems.  
  
## See Also  
 [Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [Using HL7 2.X Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)