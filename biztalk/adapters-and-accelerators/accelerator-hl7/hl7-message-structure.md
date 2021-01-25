---
description: "Learn more about: HL7 Message Structure"
title: "HL7 Message Structure | Microsoft Docs"
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
  - "trigger events"
  - "messages, trigger events"
  - "segments, messages"
  - "messages, message structure"
ms.assetid: 4dbef56d-97ae-466d-bc8a-dc96c40896f6
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# HL7 Message Structure
An HL7 message is a hierarchical structure associated with a trigger event. The HL7 standard defines trigger event as "an event in the real world of health care (that) creates the need for data to flow among systems". Each trigger event is associated with an abstract message that defines the type of data that the message needs to support the trigger event. The abstract message is a collection of segments, and includes the rules of repetition and inclusion for those segments. The following table shows an example of an abstract message associated with the trigger event A04 – Register Patient.  
  
|Trigger event|Abstract message|  
|-------------------|----------------------|  
|ADT^A04^ADT_A01|Admissions, Discharge, and Transfer|  
|MSH|Message Header|  
|EVN|Event Type|  
|PID|Patient Identification|  
|[  PD1  ]|Additional Demographics|  
|[{ ROL }]|Role|  
|[{ NK1 }]|Next of Kin / Associated Parties|  
|PV1|Patient Visit|  
|[  PV2  ]|Patient Visit - Additional Information|  
|[{ ROL }]|Role|  
|[{ DB1 }]|Disability Information|  
|[{ OBX }]|Observation/Result|  
|[{ AL1 }]|Allergy Information|  
|[{ DG1 }]|Diagnosis Information|  
|[  DRG  ]|Diagnosis Related Group|  
|[{||  
|PR1|Procedures|  
|[{ ROL }]|Role|  
|}]||  
|[{ GT1 } ]|Guarantor|  
|[{||  
|IN1|Insurance|  
|[  IN2 ]|Insurance Additional Information|  
|[{ IN3 }]|Insurance Additional Information - Cert.|  
|[{ ROL }]|Role|  
|}]||  
|[  ACC  ]|Accident Information|  
|[  UB1  ]|Universal Bill Information|  
|[  UB2  ]|Universal Bill 92 Information|  
|[  PDA  ]|Patient Death and Autopsy|  
  
 The brackets above "[", "]" indicate that a segment or group of segments is optional, while braces "{", "}" indicate the segment or group of segments repeat.  
  
 A segment is a group of fields each of which conforms to a particular data type. Fields can have a simple or complex structure. They consist of components according to the rules defined in their data-type definition. In order to support the more complex data types, some components may consist of subcomponents.  
  
> [!NOTE]
>  The fact that HL7 message encoding uses specified delimiters limits the ability of a developer to introduce new ways of subdividing the data. There can be no sub-subcomponent, since this would require invention of a new delimiter type.  
  
 The first HL7 specifications did not define the abstract message. The abstract message is the pattern of segments associated with a trigger event. Similarly, HL7 messages contain collections of segments that repeat together, or segment groups. The first HL7 specifications did not define segment groups. Starting with V2.3.1, and continuing in the subsequent versions, this changed due to the need to support XML encoding. For example, in the Trigger Event table above, the name of the message structure is "ADT_A01". This is the same pattern of segments used to support A01 – Admit Patient. For convenience, the names of message structures correspond to the first (in terms of placement within the HL7 document) trigger event that uses them. Similarly, the group of segments in the Trigger Event table above that starts with IN1, including IN2, IN3, and ROL, repeats as a group. Its name—starting with Version 2.5 is "Insurance" group.  
  
 In Version 2, the inter-version compatibility rules support evolution of interfaces by requiring that subsequent versions of the standard not include structures that invalidate prior versions. This requires that you do not remove a trigger event and that you do not use a trigger event for a different purpose or with a different abstract message than originally intended. For abstract messages, this implies that you cannot remove a segment from a message, nor can you make a mandatory segment optional or a repeating segment non-repeating. If you add a segment, you must do so at the end of a message or at the end of a repeating group within a message.  
  
 The following functions of Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) support these requirements:  
  
-   Support of all trigger events and message structures starting with V2.1 and continuing through V2.5.  
  
-   Support of localization through adding segments and tailoring segment optionally and repetition.  
  
## See Also  
 [Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [Using HL7 2.X Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)
